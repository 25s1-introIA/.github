```python

from owlready2 import *
import pandas as pd
from rdflib import Graph

# 1. Carregar ou Criar Ontologia
class IndustrialOntology:
    def __init__(self, ontology_path="ontology.owl"):
        # Carregar ou criar uma nova ontologia
        self.onto = get_ontology(ontology_path).load()
    
    def define_classes_relations(self):
        with self.onto:
            class Produto(Thing): pass
            class Categoria(Thing): pass
            class Aplicacao(Thing): pass
            
            class pertence_a(Produto >> Categoria): pass
            class usado_em(Produto >> Aplicacao): pass
    
    def save_ontology(self, path="ontology.owl"):
        self.onto.save(file=path)

# 2. Integrar Dados do E-commerce
class DataLoader:
    def __init__(self, data_path="products.csv"):
        self.data_path = data_path
        self.data = None
    
    def load_data(self):
        self.data = pd.read_csv(self.data_path)
    
    def enrich_data_with_ontology(self, ontology):
        for _, row in self.data.iterrows():
            produto = ontology.Produto(row["product_name"])
            categoria = ontology.Categoria(row["category"])
            aplicacao = ontology.Aplicacao(row["application"])
            produto.pertence_a.append(categoria)
            produto.usado_em.append(aplicacao)

# 3. Implementar o Motor de Recomendação
class RecommenderSystem:
    def __init__(self, ontology, data):
        self.ontology = ontology
        self.data = data
    
    def recommend_by_similarity(self, product_id):
        produto = self.ontology.search_one(iri=f"*{product_id}")
        if produto:
            return [p.name for p in produto.pertence_a[0].indirect_instances() if p != produto]
        return []
    
    def recommend_by_compatibility(self, product_id):
        produto = self.ontology.search_one(iri=f"*{product_id}")
        if produto:
            return [p.name for p in produto.usado_em[0].indirect_instances() if p != produto]
        return []
    
    def recommend_by_profile(self, user_id):
        # Simulação de perfil de compra
        user_purchases = self.data[self.data["user_id"] == user_id]["product_name"].tolist()
        recommendations = set()
        for prod in user_purchases:
            produto = self.ontology.search_one(iri=f"*{prod}")
            if produto:
                recommendations.update([p.name for p in produto.pertence_a[0].indirect_instances()])
        return list(recommendations)

# 4. Teste com Cesta de Produtos
class ShoppingCart:
    def __init__(self):
        self.items = []
    
    def add_item(self, product_id):
        self.items.append(product_id)
    
    def get_recommendations(self, recommender):
        recommendations = set()
        for item in self.items:
            recommendations.update(recommender.recommend_by_similarity(item))
            recommendations.update(recommender.recommend_by_compatibility(item))
        return list(recommendations)

# 5. Interface de Usuário Simples (Exemplo de Uso)
if __name__ == "__main__":
    # Criar instâncias das classes
    ontology = IndustrialOntology()
    ontology.define_classes_relations()
    
    data_loader = DataLoader()
    data_loader.load_data()
    data_loader.enrich_data_with_ontology(ontology)
    
    recommender = RecommenderSystem(ontology, data_loader.data)
    
    # Criar cesta de compras
    cart = ShoppingCart()
    cart.add_item("P1234")
    cart.add_item("P5678")
    
    # Exibir recomendações baseadas na cesta
    print("Recomendações para Cesta de Compras:", cart.get_recommendations(recommender))
    
    # Exemplo de recomendações individuais
    print("Recomendações por Similaridade:", recommender.recommend_by_similarity("P1234"))
    print("Recomendações por Compatibilidade:", recommender.recommend_by_compatibility("P1234"))
    print("Recomendações por Perfil de Usuário:", recommender.recommend_by_profile("U5678"))

```
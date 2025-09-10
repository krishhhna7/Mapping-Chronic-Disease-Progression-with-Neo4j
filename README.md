# Mapping Chronic Disease Progression with Neo4j

When I started working on a project related to predicting chronic diseases, I quickly realized that relational databases were limiting. A patient’s journey isn’t flat — it’s a network of symptoms, lifestyle habits, lab results, and treatments that evolve over time. SQL could give me rows, but it couldn’t give me relationships. That’s when I tried **Neo4j**, and it completely changed how I viewed the data.

---

## Why Graphs for Healthcare?

Imagine two patients:  
- One diagnosed with **Type 2 Diabetes**  
- Another diagnosed with **Hypertension**  

Both may share overlapping symptoms like fatigue or high blood pressure, similar lifestyle habits, and even common medications.  

In a relational table, these appear as disconnected rows.  
In Neo4j, they become a **connected journey**.  

---

## Data Model

Here’s a simplified version of my graph structure:

```cypher
(:Patient {id: 101})-[:HAS_SYMPTOM]->(:Symptom {name: "Fatigue"})
(:Patient {id: 101})-[:DIAGNOSED_WITH]->(:Disease {name: "Type 2 Diabetes"})
(:Disease {name: "Type 2 Diabetes"})-[:RESPONDS_TO]->(:Medication {name: "Metformin"})
(:Patient {id: 102})-[:HAS_LIFESTYLE]->(:Lifestyle {name: "Sedentary"})

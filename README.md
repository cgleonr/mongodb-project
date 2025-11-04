# Pokémon Data Warehouse & Analysis (MongoDB Project)

### Master’s Program – NoSQL / MongoDB Module  
**Author:** Carlos Leon 
**Environment:** Python 3.12 · Jupyter Notebook · MongoDB (local instance)

---

## Overview
This project demonstrates a complete data pipeline and analytical workflow using **MongoDB** and **Python**.  
It sources live data from the [PokéAPI](https://pokeapi.co/), stores it in MongoDB, performs modeling, transformation, and aggregation, and generates both analytical results and visualizations.

The goal is to build a Pokémon Data Warehouse, similar to a biological or ecological study database — enabling exploration of Pokémon species characteristics, habitats, and relationships.

The notebook for this project can be seen in the [pokeapi_to_mongodb.py](https://github.com/cgleonr/mongodb-project/blob/main/pokeapi_to_mongodb.ipynb) here, and as a pdf version [here]()

---

## Project Workflow

### 1. **Data Collection**
- Connected to [PokéAPI](https://pokeapi.co/) endpoints:
  - `/pokemon-species/` – species-level biological details (habitat, color, growth rate, etc.)
  - `/pokemon/` – individual Pokémon attributes (stats, abilities, height, weight, types)
  - `/pokemon-habitat/` – contextual grouping of species
- Data fetched via Python using `requests` and stored raw in MongoDB for cleaning and transformation.

### 2. **Data Modeling**
Three main **MongoDB collections** were created:

| Collection | Description |
|-------------|--------------|
| `species_clean` | Cleaned and standardized Pokémon species data |
| `pokemon_clean` | Cleaned Pokémon-specific data (stats, types, abilities) |
| `pokedex_entries` | Simplified dataset emulating a real Pokédex (name, type, height, flavor text, sprite) |

These are linked logically via common fields like `name` and `dex_number`.

### 3. **Data Cleaning & Transformation**
- Extracted relevant fields from nested JSON objects.
- Removed duplicates and missing records.
- Created derived attributes (`height_m`, `weight_kg`, etc.).
- Enforced consistent naming conventions and standardized field structures.

### 4. **Data Visualization**
Key visuals included:
- Pokémon species by *habitat and status* (regular, legendary, mythical)
- Dual-type *co-occurrence analysis*
- *Average base stats* by primary type
- *Evolution chain sizes*
- *Egg group × habitat* heatmap
- Interactive *Pokédex entry card* visual for a selected Pokémon

Each visualization was generated directly from MongoDB aggregation results using `matplotlib` and `pandas`.

### 5. *Aggregation Pipelines*
1. Average Weight (kg) by Habitat Distribution
2. Habitat distribution by legendary/mythical status
3. Type co-occurrence network
4. Average base stats per type
5. Evolution chain sizes
6. Egg-group × habitat frequency analysis

Each pipeline demonstrates different aggregation operators (e.g., `$match`, `$group`, `$project`, `$unwind`, `$sort`, `$cond`, `$arrayToObject`).

### 6. **Pokedex Simulation**
A lightweight “Pokédex” collection was built to visualize Pokémon entries with:
- Species name and genus
- Type and physical data
- Flavor text
- Sprite image and Artwork

An inline visual cell mimics an actual Pokédex entry.

### 7. **Schema Diagram**
A class diagram was created using Mermaid, representing:
- Collections (`species_clean`, `pokemon_clean`, `pokedex_entries`)  
- Their logical relationships (`name` / `species_id` links)

---

## Technologies Used

| Category | Tools |
|-----------|-------|
| Programming | Python 3.12 |
| Database | MongoDB (local instance) + Compass |
| Visualization | Matplotlib |
| Development | VS Code + Jupyter Notebook |
| API | [PokéAPI](https://pokeapi.co/) |
| Class Diagram | Via [mermaidchart.com](mermaidchart.com)|
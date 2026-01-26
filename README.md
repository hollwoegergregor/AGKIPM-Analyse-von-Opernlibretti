# AGKIPM-Analyse-von-Opernlibretti

**Ein MVRT (Minimal Viable Research Tool) zur LLM-gestützten Analyse historischer Libretti der Wiener Klassik.**

**Kurs:** LLM-unterstütztes Wissens- und Projektmanagement  
**Datum:** 26.01.2026  

## Über das Projekt
Dieses Projekt untersucht, wie historische Operntexte (Fallbeispiel: Mozarts *Die Entführung aus dem Serail*, KV 384) durch Natural Language Processing (NLP) maschinenlesbar gemacht werden können. Das Tool klassifiziert Textstellen basierend auf der **Affektenlehre von René Descartes (1649)**.

## Nutzung (Prototyp starten)
Das Tool benötigt keine Installation (Single-Page-Application). 
1. Eigene Kopie klonen oder herunterladen.
2. `index.html` im Browser öffnen.
3. Eigenen Google API-Key (Gemini 2.5 Flash) eingeben.

## Projektstruktur
- `/docs`: Das Wissensmanagement-Vault (Obsidian). Enthält System-Prompts, Projektplan und User Stories.
- `index.html`: Erster Blogpost mit dem ursprünglichen Projektdesign.
- `protoytyp.html`: Das Frontend mit der API-Schnittstelle.
- `visualisierung.html`: Das Daten-Dashboard (Chart.js & Vis.js) basierend auf den JSON-Outputs.
- `/data`: Der generierte Datensatz für den 1. Akt von KV 384.

## Tech-Stack
- **KI-Modell:** Google Gemini 2.5 Flash (via REST API)
- **Frontend:** HTML5, Vanilla JavaScript, CSS
- **Visualisierung:** Chart.js, Vis.js
- **Projektmanagement:** Obsidian (Markdown)
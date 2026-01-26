# Daten-Architektur

## 1. Input-Struktur (Syntax)

Um die Token-Effizienz zu maximieren und "Context Rot" zu vermeiden, wird das Material in Szenen-Fragmenten (< 2000 Tokens) übergeben.

### Erkennungsmuster:

- **Sprecher:** Identifiziert durch Großschreibung am Zeilenanfang gefolgt von einem Zeilenumbruch.
    
- **Regieanweisung:** Text in runden Klammern `(...)`. Diese sind bei der Affektanalyse zu priorisieren, da sie explizite Anweisungen zur Darstellung enthalten.
    

## 2. Ziel-Modell (Output JSON Schema)

Jede Analyse-Iteration MUSS das folgende Schema strikt einhalten, um die Interoperabilität zu gewährleisten:

```
{
  "unit_id": "Eindeutige ID der Szene/Arie",
  "entities": [
    {
      "name": "Standardisierter Name der Figur",
      "role": "Funktion (z.B. Herr, Diener, Vertraute)",
      "verse_type": "Arie | Rezitativ | Duett | Chor"
    }
  ],
  "analysis": {
    "primary_affekt": "Enum [Bewunderung, Liebe, Hass, Verlangen, Freude, Trauer]", 
    "confidence_score": "Float (0.0 - 1.0)",
    "intensity": "Integer (1-10)",
    "evidence": "Originalzitat als Beleg",
    "historical_context": "Kurze Einordnung basierend auf der Affektenlehre"
  },
  "relations": [
    {
      "actor": "Name des Sprechers (aus 'entities')",
      "target_entity": "Wer wird adressiert? (Anderer Figurenname, 'self' oder 'audience')",
      "interaction_type": "Art der Interaktion (z.B. Anrufung, Klage, Befehl)"
    }
  ]
}
```

## 3. Datenqualität & Transformation

### Umgang mit historischen Varianten:

- **Normalisierung:** Das LLM soll Namen normalisieren (z.B. "Osmin." -> "Osmin"), aber den Textkörper im Original belassen, um die semantische Nuancierung nicht zu verfälschen.
    
- **Fehlerbehandlung:** Unleserliche Stellen (aus OCR-Fehlern) sind als `[UNCERTAIN]` zu markieren und nicht "kreativ" durch die KI zu ergänzen.
    

## 4. Beziehungen (Kardinalität)

- Das Modell erfasst die **Sprechrichtung**.
    
- Feld: `target_entity` (Wer wird adressiert?). Falls die Figur alleine auf der Bühne steht (Monolog/Arie), ist der Wert `self` oder `audience`.
# Motivated Reasoning in GPT-2-XL

Autoren:
- 5437590, inf23160@lehre.stuttgart-dhbw.de, Tim Porger
- 4513303, inf23129@lehre.stuttgart-dhbw.de, Florentin Röseler

Datensätze:
- https://huggingface.co/datasets/cais/mmlu
- https://huggingface.co/datasets/tau/commonsense_qa
- https://huggingface.co/datasets/allenai/ai2_arc

## Setup
Installiere requirements.txt
```bash
pip install -r requirements.txt
```
## Projektübersicht

Dieses Notebook untersucht, ob **Motivated Reasoning** Effekte in Sprachmodellen ohne explizites Chain-of-Thought Reasoning nachweisbar sind. Das Projekt baut auf Anthropics Forschung zu verzerrtem Reasoning in CoT-Modellen auf und untersucht, ob ähnliche Effekte bei GPT-2 auftreten, wenn dem Modell vorgeschlagene Antworten gegeben werden.

### Forschungsfrage
Lässt sich ein ähnlicher Effekt, wie das von Anthropic beschriebene "Motivated Reasoning" auch in Modellen ohne CoT feststellen?

### Experimentelles Design

Wir testen drei Bedingungen:
1. **Neutral**: Keine Antwortvorschläge (Baseline)
2. **Correct Suggestion**: Dem Modell wird die korrekte Antwort vorgeschlagen
3. **Wrong Suggestion**: Dem Modell wird eine falsche Antwort vorgeschlagen

### Analysemethoden

1. **Accuracy-Analyse**: Wie oft antwortet das Modell in jeder Bedingung korrekt?
2. **Logit Lens**: Wie entwickeln sich die Wahrscheinlichkeiten für verschiedene Antworten über die Layers hinweg?
3. **Attention Maps**: Wie verteilt das Modell seine Aufmerksamkeit bei verschiedenen Vorschlägen?

### Datensätze
- **MMLU** (Massive Multitask Language Understanding)
- **CommonsenseQA** (Common Sense Reasoning)
- **ARC-easy** (AI2 Reasoning Challenge)

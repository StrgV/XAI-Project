# Idee

- Die Idee ist angelehnt an Kapitel 11 (Chain-of-thought Faithfulness) dieses [Anthropic Papers](https://transformer-circuits.pub/2025/attribution-graphs/biology.html#dives-cot)
    - Hier wird Reasoning von Modellen (CoT) auf "Faithfulness" untersucht
    - Also: "Führt das Modell die Schritte, welche es durch die CoT darlegt auch tatsächlich so aus?"
- Folgende interessante Ergebnisse:
    - "Faithful Reasoning" - Das Reasoning wird korrekt durchgeführt und die Antwort stimmt ebenfalls
    - Unfaithful CoTs können in zwei Fälle unterschieden werden
        1. "Bullshitting" - Das Modell liefert eine falsche Antwort (Modell halluziniert mehr oder weniger die Antwort)
        2. **Wichtig für dieses Projekt** "Motivated Reasoning" - Das Modell Arbeitet von einer vorgeschlagenen Antwort des Nutzers ausgehend Rückwärts (Evaluierbar über die Gewichtung der Input-Features), um seine Antwort zu begründen
    - Da CoT Reasoning nur mit ziemlich großen Modellen wie Claude 3.5 Haiku (sinvoll) funktioniert, wird das Untersuchungsziel etwas abgeändert
- Wir schauen uns an, ob ähnliche Effekte auch bei Modellen ohne CoT Reasoning auftreten
    - Vorschlag für ein [Untersuchungs-Modell](https://huggingface.co/openai-community/gpt2-large)
- Das Projekt und Vorgehen:
    - Wir geben dem Modell verschiedene Arten von Prompts:
        1. Prompt bei dem keine Antwort vorgegeben ist
        2. Prompt bei dem die Antwort vorgegeben und richtig ist
        3. Prompt bei dem die Antwort vorgegeben und falsch ist
    - Basierend auf den Antworten des Modells können dann verschiedene Daten evaluiert werden 
        - "Richtigkeit" der Antwort des Modells, abhängig von der gegebenen Prompt-Art
        - Welche Input-Features hat das Modell stark gewichtet, um auf die Antwort zu kommen?
            - Die Auswertung der Input-Features erfolgt mittels der Technik ["SHAP"](https://www.geeksforgeeks.org/machine-learning/shap-a-comprehensive-guide-to-shapley-additive-explanations/) evaluieren (Es gibt ein [Paper](https://transformer-circuits.pub/2025/attribution-graphs/methods.html#graphs) über die Circuit-Tracing Technik, die Anthropic dafür benutzt hat, aber das ist ziemlich sicher overkill für dieses Projekt)
            - Nachdem wir diese Infos haben lässt sich dann schauen, ob für das Modell einen unterschied macht, wenn eine Antwort mitgegeben wird und damit auch ob ein ähnlicher Effekt wie das von Anthropic beschriebene "Motivated Reasoning" vorhanden ist
- Die Forschungsfrage könnte somit (beispielsweise) lauten: "Lässt sich ein ähnlicher Effekt, wie das von Anthropic beschriebene "Motivated Reasoning" auch in Modellen ohne CoT feststellen?"

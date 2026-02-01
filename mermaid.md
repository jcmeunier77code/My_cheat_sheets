
```mermaid
graph LR
    %% Define Nodes
    Input["**Input JSON**<br/>
    {<br/>
    'commentaire_id': '125487',<br/>
    'original_text': 'Monsieur Marc Dupont est un connard de fonctionnaire'<br/>
    }"]

    Prompt{{"**System Prompt**<br/>
    Rewrite this text - return only the final text in the original language 
    - to remove all profanity and inappropriate language while preserving 
    the rest aside from identifyable information 
    - for example : names, postal addresses, phone numbers, email addresses, license plates - 
    that you have to replace according to corresponding categories, 
    for example : 
    [A CITIZEN] or [AN ADDRESS] in English, 
    [UN CITOYEN] or [UNE ADRESSE] in French, 
    [EEN BURGER] or [EEN ADRES] in Dutch."}}

    Ano_Detox{{"**Anonymize, Detoxification & Paraphrasing**<br/>
    **LLM, mistral-large+**
    model_parameters => { 'temperature': 0.0, 'max_tokens': 8192 }}}

    Output["**Output JSON**
    {
    'commentaire_id': '125487',
    'original_text': '...',
    'lang_detect': 'FR',
    'processed_text': '< UN CITOYEN > est un fonctionnaire'
    }"]

    %% Define Connections
    Input --> Prompt
    Prompt --> Ano_Detox
    Ano_Detox --> Output
    

    %% Styling
    style Input fill:#fff4e6,stroke:#f59f00,stroke-width:2px
    style Prompt fill:#e7f5ff,stroke:#1971c2,stroke-width:2px
    style Ano-Detox fill:#e7f5ff,stroke:#1971c2,stroke-width:2px
    style Output fill:#ebfbee,stroke:#2f9e44,stroke-width:2px
```

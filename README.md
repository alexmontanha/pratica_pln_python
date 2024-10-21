# Exercício: Processamento de Linguagem Natural - Tokenização e Normalização de Texto

## Objetivo

Neste exercício, você irá trabalhar com um corpus textual fornecido e desenvolver um algoritmo em Python para realizar a **tokenização** das palavras, considerando etapas comuns de **pré-processamento de texto** em problemas de Processamento de Linguagem Natural (NLP).

A atividade incluirá as seguintes tarefas:

1. **Tokenização**: Identificação de palavras distintas no texto.
2. **Normalização**: Conversão para letras minúsculas e remoção de pontuações.
3. **Remoção de palavras irrelevantes** (*stop words*).
4. **Geração de n-gramas**: Consideração de palavras como grupos (uni, bi, trigrama).
5. **Lematização**: Redução de palavras à sua raiz comum.

## Corpus Textual

O corpus que você utilizará para esta atividade é o seguinte:

```text
A Sra. Rosa plantou uma rosa no jardim. O céu estava azul e a brisa era suave. 
Ela pensou: "Seria maravilhoso se todos os dias fossem assim, tão tranquilos quanto uma rosa em flor."
```

## Instruções

1. **Tokenização**:
    - Desenvolva um algoritmo que divida o texto em tokens (palavras individuais). A princípio, considere apenas a separação por espaços, sem remoção de pontuação.

2. **Normalização de Texto**:
    - Modifique o algoritmo para remover pontuações e converter todas as palavras para letras minúsculas. Isso simplificará a análise, mas note que a perda de diferenciação semântica pode ocorrer.
    - **Exemplo**: Diferenciar entre “Sra. Rosa” (pessoa) e “rosa” (flor).

3. **Remoção de *Stop Words***:
    - Remova as palavras irrelevantes (*stop words*), como artigos ("o", "a"), preposições, etc. Você pode usar uma lista padrão de *stop words* em português ou construir sua própria.

4. **Geração de n-gramas**:
    - Implemente a criação de **n-gramas**: unigramas (1 palavra), bigramas (2 palavras), e trigramas (3 palavras). Isso permitirá uma análise mais rica do contexto.

5. **Lematização**:
    - Aplique técnicas de **lematização** para consolidar palavras com raízes semelhantes. Isso permitirá que palavras como “rosa”, “rosas” e “flor” sejam consideradas uma única entidade semântica.

## Passo a Passo

### 1. Inicializando o Projeto

- Crie um ambiente virtual para o projeto.
- Instale as bibliotecas necessárias para o exercício, como `nltk`, `spacy` ou `re`.

```bash
python -m venv venv
source venv/bin/activate  # No Windows: venv\Scripts\activate
pip install nltk spacy
```

### 2. Importando o Corpus

- Utilize a string fornecida acima para o corpus ou carregue o texto de um arquivo `.txt`.

### 3. Implementação

- **Tokenização**:
  - Use a biblioteca `nltk` ou `re` para tokenizar o texto.
  
    ```python
    import re
    text = "A Sra. Rosa plantou uma rosa no jardim. O céu estava azul e a brisa era suave."
    tokens = re.findall(r'\w+', text.lower())
    print(tokens)
    ```

- **Normalização**:
  - Use a função `re.sub()` para remover a pontuação e aplique `.lower()` para converter tudo para minúsculas.

- **Remoção de Stop Words**:
  - Utilize uma lista de *stop words* com `nltk`.

    ```python
    from nltk.corpus import stopwords
    stop_words = set(stopwords.words('portuguese'))
    filtered_tokens = [word for word in tokens if word not in stop_words]
    ```

- **n-gramas**:
  - Utilize a função `nltk.ngrams()` para gerar n-gramas a partir dos tokens.

    ```python
    from nltk import ngrams
    bigrams = list(ngrams(filtered_tokens, 2))
    trigrams = list(ngrams(filtered_tokens, 3))
    ```

- **Lematização**:
  - Utilize o `spacy` para aplicar a lematização no texto.

    ```python
    import spacy
    nlp = spacy.load('pt_core_news_sm')
    doc = nlp(" ".join(filtered_tokens))
    lemmatized = [token.lemma_ for token in doc]
    print(lemmatized)
    ```

### 4. Resultados Esperados

- Após a tokenização e o pré-processamento, você deverá ser capaz de obter:
  - Tokens normalizados e sem *stop words*.
  - n-gramas gerados para diferentes tamanhos (uni, bi, trigramas).
  - Texto lematizado, onde palavras com a mesma raiz são agrupadas.

## Entrega

- Submeta o código em um repositório Git com um arquivo `README.md` explicando a sua solução.
- Inclua os arquivos `.py` ou um `Jupyter Notebook` com o código desenvolvido.
  
Boa sorte!

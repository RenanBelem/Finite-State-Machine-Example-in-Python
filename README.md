## Verificador de Linguagem Formal (Python)

Este projeto em Python implementa um verificador de *strings* baseado nas regras de uma Linguagem Formal específica, lendo dados de entrada de arquivos de texto (`.txt`).

### Enunciado da Linguagem ($L$)

O objetivo do programa é determinar se uma *string* de entrada pertence à linguagem $L$, definida por:

$$L = \{x \mid x \in \{a, b\}^* \text{ e cada } a \text{ em } x \text{ é seguido por pelo menos dois } b\}$$

O alfabeto utilizado é $\Sigma=\{a, b, c\}$.

### Análise do Código como um Autômato Finito (AF)

O código implementa de forma **implícita** a lógica de uma **Máquina de Estados Finitos (FSM - Finite State Machine)** para reconhecer a linguagem $L$. O autômato passa por estados internos para garantir que a regra central da linguagem seja satisfeita em cada ponto da *string*.

#### Implementação da Lógica de Reconhecimento:

1.  **Regra Central:** O código verifica se **toda ocorrência** do caractere `'a'` é **imediatamente seguida** por pelo menos dois `'b'`s (`"bb"`).
2.  **Transição para Rejeição:** Se for encontrado um `'a'` que **não** é seguido por `"bb"`, o programa simula uma transição imediata para um estado de rejeição (`x = False`) e interrompe o processamento da *string* (`break`).
3.  **Aceitação:** A *string* só é considerada pertencente (`pertence!`) se for percorrida até o fim sem falhas (ou seja, `x` permanece `True`).

#### Estados Implícitos no Código:

O *loop* de verificação mantém o "estado" da validação através da posição atual (`j`) e da variável booleana `x`:

  * **Estado Inicial/Base:** A verificação continua normalmente (`x` é `True`).
  * **Estado de Falha Iminente:** Ocorre ao encontrar um `'a'`, onde o código deve obrigatoriamente verificar os próximos dois caracteres (`j+1` e `j+2`) para aceitar ou rejeitar.
  * **Estado de Rejeição/Parada:** A variável `x` se torna `False` e o *loop* é encerrado (`break`) ao falhar a condição `"bb"` após um `'a'`.

### Estrutura e Operação do Projeto

O script `main.py` foi escrito em Python e realiza as seguintes etapas:

1.  **Leitura de Arquivos:** Abre e lê o conteúdo das *strings* de três arquivos de entrada: `texto`, `texto2` e `texto3`.
2.  **Processamento:** Aplica a lógica de verificação (FSM implícita) para cada *string* lida.
3.  **Saída:** Para cada *string*, imprime o resultado no formato exigido no terminal padrão.

### Formato de Saída

A saída para cada *string* é gerada no formato:

```
[string_de_entrada]: [pertence|não pertence]!
```

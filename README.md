# Template LaTeX — Trabalhos Acadêmicos IFFar

## Créditos

Este template é uma adaptação baseada no modelo [abntex-ifpi](https://g0dkar.github.io/abntex-ifpi/) criado por **Rafael Madureira Lins de Araújo**. Essa versão foi atualizada tendo como referência o modelo para trabalhos acadêmicos disponibilizado no site do [IFFar](https://www.iffar.edu.br/component/k2/attachments/download/33182/d69cae1958128ca6e58f5f8ac3233a0e). Foram incluídas adequações e correções para funcionamento no Overleaf, suporte a referências ABNT, citação direta e diversas estilizações adicionais.

---

## Visão Geral

Template baseado no [abnTeX2](https://github.com/abntex/abntex2), adaptado para as normas do **Instituto Federal de Educação, Ciência e Tecnologia Farroupilha (IFFar)**. O arquivo principal é `documento.tex` — compile-o e seu trabalho estará pronto.

---

## Como Usar

1. Faça o download do arquivo `.zip` deste repositório;
2. Acesse o [Overleaf](https://www.overleaf.com) e clique em **New Project → Upload Project**;
3. Envie o arquivo `.zip` baixado;
4. Siga os passos indicados na seção **Primeiros Passos** abaixo para configurar seu trabalho.

---

## Estrutura de Pastas

```
.
├── documento.tex               # Arquivo principal — compile este
├── bibliografia.bib            # Banco de dados de referências BibTeX
├── abntex-iffar/               # Pacote de estilo do IFFar — não mexa aqui
│   ├── abntex-iffar.sty
│   ├── tikz-uml.sty
│   └── logo_iffar.png
├── configuracoes/              # Configurações gerais do documento
│   ├── metadados.tex           # ← Comece aqui: título, autor, curso, etc.
│   ├── tipografia.tex          # Seleção de fonte
│   ├── citacoes.tex            # Estilo de citações (autor-data ou numérico)
│   ├── cores.tex               # Definição de cores
│   ├── espacamentos.tex        # Espaçamentos do documento
│   └── pdf.tex                 # Metadados do PDF gerado
├── estrutura/
│   ├── preambulo.tex           # Carrega pacotes e configurações
│   ├── pre-textual.tex         # Ordem dos elementos pré-textuais
│   ├── textual.tex             # Lista de capítulos a incluir
│   └── pos-textual.tex         # Ordem dos elementos pós-textuais
├── pre-textual/                # Elementos pré-textuais editáveis
│   ├── resumo.tex
│   ├── resumo-lingua-estrangeira.tex
│   ├── agradecimentos.tex
│   ├── dedicatoria.tex
│   ├── epigrafe.tex
│   ├── errata.tex
│   ├── ficha-catalografica.tex
│   ├── lista-de-ilustracoes.tex
│   ├── lista-de-tabelas.tex
│   ├── siglas.tex
│   └── simbolos.tex
├── capitulos/                  # Capítulos da parte textual
│   ├── introducao.tex
│   ├── desenvolvimento.tex
│   ├── metodologia.tex
│   ├── resultados.tex
│   ├── conclusao.tex
│   └── trabalhos-futuros.tex
├── pos-textual/                # Elementos pós-textuais
│   ├── referencias.tex
│   ├── apendices.tex
│   ├── anexos.tex
│   ├── glossario.tex
│   └── indices.tex
└── imagens/                    # Coloque suas imagens aqui
```

---

## Primeiros Passos

Siga esta ordem ao começar:

1. **`configuracoes/metadados.tex`** — preencha título, subtítulo, autor, curso, campus, orientador e banca;
2. **`configuracoes/tipografia.tex`** — escolha a fonte (Arial já está ativa por ser a recomendada pelo IFFar);
3. **`pre-textual/`** — edite resumo, abstract, agradecimentos e demais elementos opcionais;
4. **`estrutura/textual.tex`** — adicione ou remova capítulos com `\input{capitulos/nome}`;
5. **`capitulos/`** — escreva o conteúdo do trabalho;
6. **`bibliografia.bib`** — adicione suas referências em formato BibTeX;
7. Compile **`documento.tex`**.

---

## Metadados (`configuracoes/metadados.tex`)

Todos os campos abaixo alimentam automaticamente a capa, folha de rosto e folha de aprovação:

```latex
\titulo{Título do Trabalho}
\subtitulo{Subtítulo (se houver)}          % Omitido se vazio
\autor{Nome do(a) Estudante}
\nomedocurso{Análise e Desenvolvimento de Sistemas}
\nomedocampus{Campus Santa Maria}
\local{Santa Maria, RS}
\tipotrabalho{Monografia}
\orientador{Prof. Dr(a). Nome do Orientador}
\data{2026}
\membroum{Prof. Me. Nome do Primeiro Membro}
\membrodois{Prof. Me. Nome do Segundo Membro}
% \membrotres{...}                         % Descomente se houver terceiro membro
\dataapresentacao{\underline{\hspace{1.0cm}}/\underline{\hspace{1.0cm}}/\underline{\hspace{1.75cm}}}
```

O preâmbulo do trabalho é gerado automaticamente a partir do tipo de trabalho, curso e campus:

```latex
\preambulo{Trabalho de Conclusão de Curso (\imprimirtipotrabalho{}) apresentado
como exigência parcial para obtenção do diploma do Curso de \imprimirnomedocurso{}
do Instituto Federal de Educação, Ciência e Tecnologia Farroupilha, \imprimirnomedocampus{}.}
```

---

## Adicionando Novos Pacotes

Adicione novos pacotes em **`estrutura/preambulo.tex`**, na seção de pacotes, usando:

```latex
\usepackage{nome-do-pacote}
```

Pacotes já incluídos por padrão: `graphicx`, `float`, `booktabs`, `multirow`, `xcolor`, `hyperref`, `pdfpages`, `tikz-uml`, `enumitem`, entre outros. Verifique antes de adicionar duplicatas.

---

## Adicionando e Removendo Capítulos

Edite **`estrutura/textual.tex`**:

```latex
\input{capitulos/introducao}
\input{capitulos/meu-novo-capitulo}   % ← adicione assim
% \input{capitulos/resultados}        % ← comente para remover
```

Crie o arquivo correspondente em `capitulos/` com o comando `\chapter{Nome}` no início.

---

## Exemplos LaTeX

### Citação curta (até 3 linhas)

```latex
Segundo \cite{autor2023}, o fenômeno ocorre em contextos específicos.

Estudos recentes apontam para novos resultados \cite{autor2023}.

% Com número de página:
\cite[p.~45]{autor2023}
```

### Citação direta longa (mais de 3 linhas)

```latex
\begin{citacao}
Texto da citação com mais de três linhas deve ser destacado com recuo
de 4 cm da margem esquerda, fonte menor e sem aspas, conforme norma
\cite[5.3]{NBR10520:2002}.
\end{citacao}
```

### Figura

```latex
\begin{figure}[htb]
    \caption{\label{fig:minhaFigura}Legenda da figura acima da imagem}
    \begin{center}
        \includegraphics[scale=0.6]{imagens/nome-do-arquivo.png}
    \end{center}
    \legend{Fonte: elaborada pelo autor, 2026}
\end{figure}

% Referência no texto:
conforme a \autoref{fig:minhaFigura}
```

### Tabela simples

```latex
\begin{table}[htb]
\ABNTEXfontereduzida
\caption[Título curto para lista]{Título completo da tabela.}
\label{tab:minhaTabela}
\begin{tabular}{l|c|r}
    \textbf{Coluna A} & \textbf{Coluna B} & \textbf{Coluna C} \\
    \hline
    Dado 1 & Dado 2 & Dado 3 \\
    \hline
\end{tabular}
\legend{Fonte: elaborada pelo autor, 2026}
\end{table}
```

### Tabela padrão IBGE

```latex
\begin{table}[htb]
\IBGEtab{
    \caption{Título da tabela padrão IBGE.}
    \label{tab:ibge}
}{
    \begin{tabular}{ccc}
    \toprule
    Nome & Nascimento & CPF \\
    \midrule \midrule
    Maria Silva & 01/01/2000 & 000.000.000-00 \\
    \bottomrule
    \end{tabular}
}{
    \fonte{Produzido pelos autores.}
    \nota{Nota explicativa, se necessário.}
}
\end{table}
```

### Listas

```latex
% Lista com marcadores
\begin{itemize}
    \item Primeiro item;
    \item Segundo item.
\end{itemize}

% Lista numerada
\begin{enumerate}
    \item Primeiro item;
    \item Segundo item.
\end{enumerate}

% Lista com letras (requer \usepackage{enumitem})
\begin{enumerate}[label=\alph*)]
    \item Justificativa;
    \item Definição do problema;
    \item Objetivo geral e objetivos específicos.
\end{enumerate}
```

### Seções e subseções

```latex
\chapter{Título do Capítulo}
\section{Seção Secundária}
\subsection{Seção Terciária}
\subsubsection{Seção Quaternária}

% Habilitar nível quaternário numerado:
\setcounter{secnumdepth}{4}
```

### Nota de rodapé

```latex
Conforme a norma\footnote{Texto explicativo da nota de rodapé, com fonte reduzida
e separado do texto por filete de 5 cm.}.
```

### Diagrama UML com TikZ-UML

O template já inclui o pacote `tikz-uml` para criação de diagramas UML diretamente em LaTeX:

```latex
\begin{tikzpicture}
\umlclass{MinhaClasse}{
    - atributo : String
}{
    + metodo() : void
}
\end{tikzpicture}
```

### Referência cruzada

```latex
% Referenciar qualquer elemento com \label:
conforme a \autoref{fig:minhaFigura}
veja a \autoref{tab:minhaTabela}
no \autoref{cha:desenvolvimento}
```

---

## Fonte

A fonte padrão é **Arial** (`helvet`), conforme recomendado pelo manual de formatação do IFFar. Para trocar, edite `configuracoes/tipografia.tex` comentando a linha ativa e descomentando outra opção disponível (Times, Palatino, Latin Modern etc.).

---

## Referências Bibliográficas

Adicione entradas no arquivo `bibliografia.bib` no formato BibTeX:

```bibtex
@book{sobrenome2023,
    Author = {Silva, João},
    Title  = {Título do Livro},
    Publisher = {Editora},
    Address = {Cidade},
    Year = {2023}
}

@article{autor2022,
    Author  = {Souza, Maria},
    Title   = {Título do Artigo},
    Journal = {Nome da Revista},
    Volume  = {10},
    Number  = {2},
    Pages   = {15--30},
    Year    = {2022}
}
```

Cite no texto com `\cite{sobrenome2023}` ou `\citeonline{sobrenome2023}` (para citações integradas à frase).

---

## Elementos Pré-textuais

Definidos em `estrutura/pre-textual.tex`, na seguinte ordem obrigatória conforme normas do IFFar:

| # | Elemento | Obrigatoriedade |
|---|----------|----------------|
| 1 | Capa | Obrigatório |
| 2 | Folha de rosto | Obrigatório |
| 3 | Errata | Opcional |
| 4 | Folha de aprovação | Obrigatório |
| 5 | Dedicatória | Opcional |
| 6 | Agradecimentos | Opcional |
| 7 | Epígrafe | Opcional |
| 8 | Resumo | Obrigatório |
| 9 | Abstract | Obrigatório |
| 10 | Lista de ilustrações | Opcional |
| 11 | Lista de tabelas | Opcional |
| 12 | Lista de siglas | Opcional |
| 13 | Lista de símbolos | Opcional |
| 14 | Sumário | Obrigatório |

Para desativar um elemento opcional, comente a linha correspondente em `estrutura/pre-textual.tex`.

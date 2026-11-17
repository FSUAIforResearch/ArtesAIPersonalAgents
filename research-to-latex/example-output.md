# Example Output: Research-to-LaTeX Agent

Below is an example of what your ArtesAI **Research-to-LaTeX Agent** will generate when given the prompt in [`example-input.md`](./example-input.md):

Output generated on 2026/11/16 with ArtesAI using model gpt-5.6-luna.
---

## Proposed Structure

1. Title and abstract  
2. Objective  
3. Methods  
4. Results, including the supplied table  
5. Reported equation  
6. Code excerpt  
7. Discussion  
8. Limitations  

The missing author information, citation, and workflow diagram are marked as TODOs rather than being invented.

## Complete LaTeX Source

```latex
\documentclass[11pt]{article}

\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage{lmodern}
\usepackage{amsmath}
\usepackage{booktabs}
\usepackage{listings}
\usepackage{geometry}

\geometry{margin=1in}

\lstset{
  language=Python,
  basicstyle=\ttfamily\small,
  columns=fullflexible,
  keepspaces=true,
  frame=single,
  breaklines=true
}

\title{Comparing Two Document Conversion Workflows}

% TODO: Supply the author name and affiliation.
\author{}
\date{}

\begin{document}

\maketitle

\begin{abstract}
This pilot compares the time required to prepare editable LaTeX drafts from Markdown notes using Workflow A and Workflow B. Each workflow was applied once to each of six sample reports. Workflow B had a lower reported mean preparation time in this pilot, but no significance tests, confidence intervals, or effect sizes were computed.
\end{abstract}

\section{Objective}

The objective was to compare the time required to prepare editable LaTeX drafts from Markdown notes using Workflow A and Workflow B.

\section{Methods}

Each workflow was applied to the same 6 sample Markdown reports. Each report contained one table and one equation. Each workflow was run once per report. Preparation time included manual correction of the generated LaTeX. Hardware and software versions were not recorded.

\section{Results}

The recorded values are shown in Table~\ref{tab:results}.

\begin{table}[htbp]
  \centering
  \caption{Preparation-time and manual-correction results.}
  \label{tab:results}
  \begin{tabular}{lrrr}
    \toprule
    Workflow & Reports processed & Mean preparation time (min) & Reports requiring manual correction \\
    \midrule
    A & 6 & 18.5 & 4 \\
    B & 6 & 12.0 & 2 \\
    \bottomrule
  \end{tabular}
\end{table}

\subsection{Reported Equation}

Mean preparation time was defined as
\begin{equation}
  \bar{t} = \frac{1}{n}\sum_{i=1}^{n} t_i.
  \label{eq:mean-time}
\end{equation}

Here, $t_i$ is preparation time for report $i$, measured in minutes, and $n$ is the number of reports.

\subsection{Code Excerpt}

This Python excerpt labels the two workflows; it does not perform analysis:

\begin{lstlisting}
workflow_labels = ["A", "B"]
print("Workflow labels:", workflow_labels)
\end{lstlisting}

\section{Discussion}

Workflow B had a lower reported mean preparation time in this pilot. No significance tests, confidence intervals, or effect sizes were computed. These observations do not establish a general performance advantage.

Structured authoring workflows can support reproducible document preparation \cite{TODO}.

% TODO: A workflow diagram was mentioned in the planning notes, but no figure file was supplied. Do not add a figure until the file is provided.

\section{Limitations}

Only 6 reports were included. Each workflow was run once per report. Hardware and software versions were not recorded. Manual corrections were included in preparation time but were not categorized by error type.

\end{document}
```

## Researcher Checklist

- Supply the author name and affiliation.
- Replace `\cite{TODO}` with a real citation after a source is identified.
- Add a bibliography only after the corresponding bibliographic data is supplied.
- Provide the workflow diagram file if it should appear in the report.
- Confirm that the exact installed Python and LaTeX environments support the intended compilation workflow.
- Compile with pdfLaTeX and verify table layout, code formatting, and equation rendering.
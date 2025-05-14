---
title: Execution
layout: home
nav_order: 4
parent: Home
---

\section{Running HYMET}

After completing the initial setup and configuration, you can run the HYMET tool using the main script. Follow these steps:

\begin{enumerate}
    \item Execute the main script:
    
\begin{lstlisting}[language=bash]
./main.pl
\end{lstlisting}

    \item When prompted, enter the path to the input directory containing your .fna files:
    
\begin{lstlisting}[language=bash]
Please enter the path to the input directory (containing .fna files): 
\end{lstlisting}
    
    \item Type or paste the full path to your input directory and press Enter.
\end{enumerate}

The tool will then process the input files and perform the taxonomic identification based on the configured databases and taxonomy files.

\textbf{Note:} Ensure that your input directory contains properly formatted .fna files before running the tool.

\subsection{Mash Threshold and Candidate Selection}

The \texttt{mash} tool is used in the pipeline to screen input sequences and select candidate genomes for further analysis. The threshold parameter plays a crucial role in balancing the number of candidates selected and the computational load of subsequent steps.

\subsubsection*{Default Threshold and Candidate Calculation}

In this pipeline, the default threshold is set to \texttt{3.25}, meaning that for each input sequence, approximately 3.25 candidate genomes are selected. This ensures a balance between sensitivity and computational efficiency. The number of candidates is calculated as:

\begin{lstlisting}[language=bash]
min_candidates=$(echo "$num_sequences * 3.25" | bc | awk '{printf("%d\n",$1 + 0.5)}')
min_candidates=$(( min_candidates < 5 ? 5 : min_candidates ))
\end{lstlisting}

Here:
\begin{itemize}
    \item \texttt{\$num\_sequences}: The total number of input sequences in the directory.
    \item \texttt{3.25}: The default multiplier for candidate selection.
    \item A minimum of 5 candidates is enforced, even for small datasets.
\end{itemize}

\subsubsection*{Adjusting the Threshold}

The threshold can and should be adjusted based on the type and size of the input data:

\begin{itemize}
    \item For datasets with large genomes (e.g., vertebrates) or high computational constraints: Use a lower multiplier, such as \texttt{1.25-2.25}, to avoid overloading subsequent steps in the pipeline.
    \item For datasets with small genomes (e.g., prokaryotes or micro-eukaryotes) or when higher classification accuracy is desired: Use a higher multiplier, such as \texttt{4.25-5.25}, to increase precision and accuracy in classification.
    \item For very large datasets (more than 1000 query sequences): Reduce the multiplier to \texttt{1.25-2.0} to avoid excessive computational load.
\end{itemize}

By carefully adjusting the threshold based on your dataset's characteristics, you can optimize both computational efficiency and classification accuracy.

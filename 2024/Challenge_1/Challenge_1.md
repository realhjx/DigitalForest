\documentclass[12pt]{article}
\usepackage[a4paper, margin=1in]{geometry}
\usepackage{amsmath, amssymb}
\usepackage{enumitem}

\title{\textbf{The Digital Forest}\\
\large Part 1: The Password Guardian Device}

\author{Realhjx}
\date{01.12.2024}

\begin{document}

\maketitle

\section*{Story}

Deep within the heart of the Digital Forest lies an ancient \textbf{Password Guardian Device}, a critical system that safeguards the secrets of the forest. This device displays a four-digit code on a seven-segment display, ensuring that only the worthy can access the treasures in the forest.

However, the logic controlling this device has malfunctioned, putting the entire forest at risk. As an expert FPGA engineer, you have been asked to design a new control logic to restore the device's functionality and secure the forest once more.

\section*{Mission Objectives}

You must design an FPGA-based control logic to meet the following requirements:

\subsection*{Part 1: Counting Logic}

\begin{enumerate}[label=\textbf{\arabic*.}]
    \item \textbf{Counting Mode:}
    \begin{itemize}
        \item When \textbf{Switch[0] and Switch[1] are both 0}, pressing \textbf{Button[0]} will increment the number displayed on the four-digit seven-segment display by 1.
        \item The count should loop from \texttt{0000} to \texttt{9999} and then back to \texttt{0000}.
    \end{itemize}
    
    \item \textbf{Reset Mode:}
    \begin{itemize}
        \item When \textbf{only Switch[0] is set to 1}, the display should reset to \texttt{0000}, regardless of other inputs.
    \end{itemize}
    
    \item \textbf{Freeze Mode:}
    \begin{itemize}
        \item When \textbf{only Switch[1] is set to 1}, the display should freeze at its current value.
        \item Pressing \textbf{Button[0]} in this state should have no effect.
        \item Additionally, \textbf{LED[0]} should light up to indicate the system is in freeze mode.
    \end{itemize}
    
    \item \textbf{Lockdown Mode:}
    \begin{itemize}
        \item When \textbf{Switch[0] and Switch[1] are both 1}, the display should freeze at \texttt{0000}.
        \item \textbf{LED[0]} should remain lit, indicating the system is in lockdown mode.
    \end{itemize}
\end{enumerate}

\subsection*{Part 2: Random Password Generation}

In this part, the logic will be extended to allow random password generation on the seven-segment display.

\begin{enumerate}[label=\textbf{\arabic*.}]
    \item \textbf{Random Password Mode:}
    \begin{itemize}
        \item When \textbf{Switch[0] and Switch[1] are both 0}, pressing \textbf{Button[0]} should generate a new pseudo-random number between \texttt{0000} and \texttt{9999} as password.
        \item Ensure that the password appears instantly on the display with no flickering.
    \end{itemize}
    \item \textbf{Security Mode:}
    \begin{itemize}
        \item When \textbf{only Switch[0] is set to 1}, the display should set to \texttt{0000} to protect the password, regardless of other inputs.
        \item The password displayed before entering Security Mode should be saved. When exiting Security Mode (Switch[0] is reset to 0), the display should restore the previously saved password.
    \end{itemize}
    \item \textbf{Freeze Mode:}
    \begin{itemize}
        \item When \textbf{only Switch[1] is set to 1}, the password should freeze at its current value.
        \item Pressing \textbf{Button[0]} in this state should have no effect.
        \item Additionally, \textbf{LED[0]} should light up to indicate the system is in freeze mode.
    \end{itemize}
    
    \item \textbf{Lockdown Mode:}
    \begin{itemize}
        \item When \textbf{Switch[0] and Switch[1] are both 1}, the display should freeze at \texttt{0000} to enforce lockdown.
        \item The password displayed before entering Lockdown Mode should be saved. When the device is switched from Lockdown Mode to Freeze Mode, the display should restore the previously saved password.
        \item \textbf{LED[0]} should remain lit, indicating the system is in lockdown mode.
    \end{itemize}
\end{enumerate}

\section*{Constraints}

\begin{itemize}
    \item All the specified logic must be implemented on an FPGA development board using a hardware description language (HDL).
    \item The implementation should use \textbf{switches} and \textbf{buttons} as input devices, and \textbf{seven-segment displays} and \textbf{LED} as output devices.
\end{itemize}


\section*{Challenge Yourself}

The fate of the Digital Forest depends on you! Step into the role of the guardian engineer and use your FPGA skills to restore order to the system. Prove yourself as the hero of the Digital Forest!

\end{document}

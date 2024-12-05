\documentclass[12pt]{article}
\usepackage[a4paper, margin=1in]{geometry}
\usepackage{amsmath, amssymb}
\usepackage{enumitem}

\title{\textbf{The Digital Forest}\\
\large Part 2: The Battle Oracle}

\author{Realhjx}
\date{05.12.2024}

\begin{document}

\maketitle

\section*{Story}

After restoring the \textbf{Password Guardian Device}, you delve deeper into the \textbf{Digital Forest}. You discover the \textbf{Battle Oracle}, a device once used to settle disputes among the forest's ancient inhabitants through a strategic game of \textbf{Digital Rock-Paper-Scissors}. The Oracle's malfunctioning logic has plunged the forest into disarray, and only you can restore its fairness and functionality. 

Your mission is to design the control logic for this game using an FPGA, ensuring the Oracle once again brings order and balance to the forest.

\section*{Mission Objectives}

Design an FPGA-based system to implement the \textbf{Digital Rock-Paper-Scissors} game with the following features:

\subsection*{Game Setup}

\begin{enumerate}[label=\textbf{\arabic*.}]
    \item \textbf{Pre-game Mode:}
    \begin{itemize}
        \item Before the game begins, all \textbf{eight seven-segment displays} must remain lit with the pattern \texttt{88888888}.
        \item All \textbf{16 LEDs} (indicating player's remaining lives) should remain turned on.
        \item This state continues until the player presses \textbf{Button[0]}, signaling the start of the game.
    \end{itemize}


\end{enumerate}

\subsection*{Game Rounds}

Each round follows these steps:

\begin{enumerate}[label=\textbf{\arabic*.}, resume]

    \item \textbf{Countdown:}
    \begin{itemize}
        \item Upon pressing \textbf{Button[0]}, the \textbf{seven-segment displays} must display a countdown starting from \texttt{5}, decrementing every second until it reaches \texttt{0}.
        \item During the countdown, players can input their choices via the switches.
    \end{itemize}
    \vspace{0.5\baselineskip}
    \item \textbf{Player Input:}
    \begin{itemize}
        \item \textbf{Player A} uses switches \textbf{SWITCH[0] to SWITCH[2]} to select their move:
            \begin{itemize}
                \item \texttt{SWITCH[0]}: Rock.
                \item \texttt{SWITCH[1]}: Paper.
                \item \texttt{SWITCH[2]}: Scissors.
            \end{itemize}
        \item \textbf{Player B} uses switches \textbf{SWITCH[15] to SWITCH[13]} for their move:
            \begin{itemize}
                \item \texttt{SWITCH[15]}: Rock.
                \item \texttt{SWITCH[14]}: Paper.
                \item \texttt{SWITCH[13]}: Scissors.
            \end{itemize}
        \item Players must select exactly one switch (high level) to indicate their choice.
    \end{itemize}


    \item \textbf{Outcome Determination:}
    \begin{itemize}
        \item The outcome is decided based on standard Rock-Paper-Scissors rules:
        \begin{itemize}
            \item Rock beats Scissors.
            \item Scissors beats Paper.
            \item Paper beats Rock.
        \end{itemize}
        \item If a player selects more than one switch or no switch at all, they are considered to have made an invalid input and automatically lose the round. If both players provide invalid inputs, the round ends in a draw, and no lives are deducted.
        
        \item The losing player loses one life, and their corresponding LED indicates this:
        \begin{itemize}
            \item For \textbf{Player A}, the LEDs representing lives are \textbf{LED[7] to LED[0]}. Each time Player A loses, the \textbf{innermost active LED} (starting from LED[7] and moving sequentially towards LED[0]) is turned off.
            \item For \textbf{Player B}, the LEDs representing lives are \textbf{LED[8] to LED[15]}. Each time Player B loses, the \textbf{innermost active LED} (starting from LED[8] and moving sequentially towards LED[15]) is turned off.
        \end{itemize}
        \item In the event of a draw, no LEDs are turned off for either player.
    \end{itemize}


    \item \textbf{Next Round:}
    \begin{itemize}
        \item To begin the next round, the player must press \textbf{Button[0]} again.
        \item This triggers the \textbf{seven-segment display} countdown to restart from \texttt{5}.
    \end{itemize}
\end{enumerate}

\subsection*{Game End}

\begin{enumerate}[label=\textbf{\arabic*.}, resume]
    \item \textbf{Victory Condition:}
    \begin{itemize}
        \item The game ends when one player's lives (indicated by their LEDs) are fully depleted.
        \item The winner's \textbf{RGB light} will flash every 0.5 seconds to celebrate their victory:
        \begin{itemize}
            \item For \textbf{Player A}, the RGB light is \textbf{RGB[0]}.
            \item For \textbf{Player B}, the RGB light is \textbf{RGB[1]}.
        \end{itemize}
    \end{itemize}



    \item \textbf{Reset Functionality:}
    \begin{itemize}
        \item Pressing \textbf{Button[1]} at any time returns the system to the pre-game mode:
        \begin{itemize}
            \item The \textbf{seven-segment displays} return to the pattern \texttt{88888888}.
            \item All \textbf{16 LEDs} turn on.
        \end{itemize}
    \end{itemize}
\end{enumerate}

\section*{Constraints}

\begin{itemize}
    \item All the specified logic must be implemented on an FPGA development board using a hardware description language (HDL).
    \item The implementation should use \textbf{switches} and \textbf{buttons} as input devices, and \textbf{seven-segment displays}, \textbf{LEDs} and \textbf{RGB lights} as output devices.
\end{itemize}

\section*{Challenge Yourself}

The Digital Forest has entrusted you with its most sacred device. Will you rise to the challenge and prove yourself as the master engineer? Design the logic for the \textbf{Battle Oracle} and bring justice and harmony back to the forest!

\end{document}

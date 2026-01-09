# Comparing PID and MPC for Cruise Control

\section*{Results and Discussion Overview}

In this final section, we will discuss three types of scenarios in an Adaptive Cruise Control (ACC) system and test them to ensure that the system is working as expected.

\subsection*{1. Performance Benchmarking}
\begin{itemize}
    \item We test the system using the same conditions as the Matlab documentation where $V_{set} = 30 \text{ m/s}$.
    \item This confirms our PID tuning is correct and can follow a lead vehicle accurately.
    \item It shows the car handles non-linear drag while keeping a safe distance.
\end{itemize}

\subsection*{2. High-Speed Highway Test}
\begin{itemize}
    \item We increase the speed to highway levels (e.g., $40 \text{ m/s}$) to test the car under more stress.
    \item This helps us see how aerodynamic drag affects the controller at higher velocities.
    \item We observe if the PID can still maintain the safety gap when air resistance is high.
\end{itemize}

\subsection*{3. Road Grade Disturbance (The Hill)}
\begin{itemize}
    \item We place the ego vehicle on a hill while the lead car stays on flat ground.
    \item This tests how well the controller handles gravity pulling the car backward.
    \item We prove the Integral ($I$) term works to add extra throttle to stay at the correct distance.
\end{itemize}

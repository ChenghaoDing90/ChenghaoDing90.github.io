# Houston Solar Plant Investment Study

## Objective (Solar System Cost Analysis)

How much an energy system cost is a very important standard to judge if this solar storage setup is good or not? In this example, I will discover the power of mathematical optimization in addressing a common energy industry problem: solar storage setup cost analysis. 

The current ERCOT solar grid will be evaluated based on the historical Houston Hub settlement point price along with the normalized solar output in 2019.

---
## Problem Description

In this problem, a renewable energy developer want to make an investment to a new solar farm in Houston. However, they want to know what kind of configurations is most economical and beneficial for them. Therefore, an analysis on how much they would earn in 2019 by comparing three different configurations is implemented. Here, those three configurations are respectively (1) standalone storage system; (2) solar+storage system (3) standalone solar. 

The data set of 8760 hourly solar irradiance and Houston hub electricity price is as follows:

| weather year hour beginning | Solar Shape (Normalized) | Houston hub Settlement Point Energy Price (\$/MWh) |
| --- | --- | ---| 
| 1/1/2019 0:00| 0 | 14.1900	 | 
| 1/1/2019 1:00 | 0 | 15.1825	 |
| 1/1/2019 2:00 | 0 | 15.5300 | 


(1) Proposed Installation (Standalone Solar) Setting:

| Parameter | Value| Unit |
| --- | --- | --- | 
| Solar Size | 300 |  MW | 
| Inverter Capacity | 220 | MW |
| Solar System Cost | \$1.45 | \$/Watt-DC |


(2) Proposed Installation (Standalone Storage) Setting:

| Parameter | Value| Unit |
| --- | --- | --- | 
| Storage Capacity | 50 |  MW | 
| Storage Energy | 200 | MWh |
| Round Trip Efficiency | 85\% |   |
| Storage System Cost | \$350 | \$/KWh  |

(3) Proposed Installation (Combined Solar + Storage System) Setting:

| Parameter | Value| Unit |
| --- | --- | --- | 
| Solar Size | 300 |  MW | 
| Inverter Capacity | 220 | MW |
| Storage Capacity | 50 |  MW |
| Storage Energy | 200 | MWh  |
| Round Trip Efficiency | 85\% |  |
| Solar System Cost | \$1.35 | \$/Watt-DC  |
| Storage System Cost | \$325 | \$/KWh  |

---

## Model Formulation

### Parameters
$\text{RTM} \in \mathbb{R}^+$: Real Time Market Settlement Point Price  \$/KWh.

normSolar: Normalized Solar Shape.

timeStamp: hours begining in year 2019.

Life cycle of Solar Pannel: assume 30 years in service.

Life cycle of Battery Storage: assume 10 years in service.

$\eta$: Round Trip Efficiency

$SOC_t$: State of Charge at hour t

$AC_t$: AC output of solar energy at hour t

$DC_t$: DC output of solar energy at hour t

### Decision Variables

$SOC_t$: State of Charge at hour t

$E_t^{in}$: Energy delivered to the storage at hour t

$E_t^{out}$: Energy discharged to the grid at hour t

$E_t^{Gin}$ : Energy charged to the storage from grid at hour t

$E_t^{BoutG}$ : Energy discharged to the grid from storage at hour t

$E_t^{Sin}$ : Energy delivered to the storage from solar at hour t

$E_t^{SoutG}$   : Energy delivered to the grid from solar at hour t


### Objective Function

- **𝑅𝑒𝑣𝑒𝑛𝑢𝑒**: Maximize the revenue of solar system (in USD).

For a standalone solar system (Assume 30 years solar plant life):

\begin{equation}
\text{Maximize}  AC_t \times P_t
\end{equation}

For a standalone storage system (Assume 10 years storage life):

\begin{equation}
\text{Maximize}  (E_t^{out}- E_t^{in}) \times P_t
\end{equation}

For a solar and storage system (Assume 10 years storage life, 30 years solar plant life):

\begin{equation}
\text{Maximize} (E_t^{BoutG}+E_t^{SoutG})∗P_t− E_t^{Gin}∗P_t
\end{equation}

### Constraints

For a standalone solar system:

$DC_t$ = 300*normSolar

$AC_t$ = min(220, $DC_t$)

For a standalone storage system:
(1) at any time t, the SOC will follow
\begin{equation}
SOC_t=SOC_{t-1}+\sqrt{\eta}\times E_{t-1}^{in}-E_{t-1}^{out}
\end{equation}

(2) $\forall t$, $0<=SOC_t<=200$.

(3) $\forall t$, $0<=\sqrt{\eta}\times E_{t}^{in}<=50$.

(4) $\forall t$, $0<=E_{t}^{out}<=50$.

(5) $\forall t$, $0<=E_{t}^{out}<=SOC_t$.

For a system combined solar and battery storage:

(1) at any time t, the SOC will follow
\begin{equation}
SOC_t=SOC_{t-1}+ (E_{t-1}^{Gin}+E_{t-1}^{Sin})-E_{t-1}^{BoutG}
\end{equation}

(2) $\forall t$, $0<=SOC_t<=200$.

(3) $\forall t$, $0<=(E_{t}^{Gin}+E_{t}^{Sin}) <=50$.

(4)  $\forall t$, $0<=E_{t}^{BoutG}<=50$.

(5)  $\forall t$, $0<=E_{t}^{BoutG}<=SOC_t$.

---
## Python Implementation

We import the Pyomo and Gurobi Python Module and other Python libraries such as pandas, NumPy.

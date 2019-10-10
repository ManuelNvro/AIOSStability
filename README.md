# AIOSStability

This project is intended to reproduce 12 stability scenarios for the "All-In-One-System" (AIOS) using Modelica and the OpenIPSL library. The scenarios are:

## 1
**Simulation time:** 10 secs. <br/> 
**Power Flow:** 1.  <br/> 
**Disturbance:** None. <br/> 
**Observations:** System equilibrium. <br/>

![alt text](https://github.com/ManuelNvro/AIOSStability/blob/master/Figures/OneDiagram.png)
![alt text](https://github.com/ManuelNvro/AIOSStability/blob/master/Figures/OnePQ.png)

## 2
**Simulation time:** 10 secs. <br/>
**Power Flow:** 1. <br/>  
**Disturbance:** Fault applies at t = 1.00 secs. at Bus 3 and clear by opening a circuit between Bus 1 and Bus 3 at t = 1.14 secs. <br/>
**Observations:** Fault lasts for 0.14 secs. The fault is really short and it preserves stability, the system will return to a new equilibrium. <br/>

## 3
**Simulation time:** 10 secs. <br/>
**Power Flow:** 1. <br/>  
**Disturbance:** Same fault ast #1, however, fault now lasts for t = 0.15 secs. <br/>
**Disturbance Changes:** Change time from t = 1.14 secs. to 1.15 secs. in two places.<br/>
**Observations:** The fault is too long now, the generator will loose synchronism. This is an example of transient (angle) instability. <br/>

## 4
**Simulation time:** 15 secs. <br/>
**Power Flow:** 2. <br/>  
**Disturbance:** Sever disturbance is consideres, two circuits are tripped between Bus 1 and Bus 3 at t = 1.00 secs.<br/>
**Observations:** The generator and load are now "islanded". The power consumed by the load is P = 400 MW while the generator capacity is P = 450 MW. The governor is able to restore the frequency close to its nominal value, allowing operation of the island to continue. <br/>

## 5
**Simulation time:** 10 secs. <br/>
**Power Flow:** 3. <br/>  
**Disturbance:** Same distrubance as #4, however, now the power consumed by the load is P = 500 MW. <br/>
**Observations:** The power demanded by the load, the generator cannot provide. The frequency decay cannot be stopped. This shows a case of frequenc instability. <br/>

## 6
**Simulation time:** 10 secs. <br/>
**Power Flow:** 4. <br/>  
**Disturbance:** A severe disturbance is considered, this consists of tirpping the generator as well as one circuit betwen Bus 1 and Bus 3 at t = 1.00 secs. <br/>
**Observations:** The motor (load at Bus 4), stalls and the voltages collapse. This shows a case of short-term voltage instability, there is a loss of short-term equilibrium. <br/>

## 7
**Simulation time:** 10 secs. <br/>
**Power Flow:** 4. <br/>  
**Disturbance:** Fault is applied at  t = 1.00 at Bus 3 and cleared by one circuit opening between Bus 1 and Bus 3 at t = 1.15 secs.<br/>
**Disturbance Changes:** Change time from t = 1.14 secs. to 1.15 secs. in two places.<br/>
**Observations:** The fault lasts t - 0.12 secs. The fault is short enough to preserve stability and the system retursn to a new equilibrium point. <br/>

## 8
**Simulation time:** 10 secs. <br/>
**Power Flow:** 4. <br/>  
**Disturbance:** Same fault is applied at #7. Now, the fault lasts for t = 0.16 secs. <br/>
**Disturbance Changes:** Change time from t = 1.14 secs. to 1.15 secs. in two places.<br/>
**Observations:** The fault lasts too long and the motor (load at Bus 4) stalls, and causes voltage collapse. This shows a case of short-term instability. This is due to a lack of attraction towards post disturbance short-term equilibrium.<br/>

## 9
**Simulation time:** 60 secs. <br/>
**Power Flow:** 5. <br/>  
**Disturbance:** Once circuit between Bus 1 and Bus 3 is tripped at t = 1.00 secs. <br/>
**Observations:** The automatic tap changer restores the voltage at the load us within the deadband. This happens withing 2 steps and the system response is stable.<br/>

## 10
**Simulation time:** 250 secs. <br/>
**Power Flow:** 6. <br/>  
**Disturbance:** Same fault as #9, however, the disturbance has a higher load.<br/>
**Observations:** The overexcitation limiter of the generator is triggered and the generator voltage is no longer controlled at t = 60 secs. From there on, the automatic tap changer tries to restore the voltage at the load bus but without success.
The voltage decreases monotonically. A case of long-term voltage instability (by loss of long-term equilibrium). The short-
term dynamics remains stable. The system degradation stops when the tap changer reaches its limit.<br/>

## 11
**Simulation time:** 180 secs. <br/>
**Power Flow:** 7. <br/>  
**Disturbance:** Same disturbance as #10.<br/>
**Observations:** However, the long-term voltage instability triggers and instability of the hsort-term dynamis in the form of a loss of synchronism of the generator. <br/>

## 12
**Simulation time:** 70 secs. <br/>
**Power Flow:** 8. <br/>  
**Disturbance:** Same disturbance as #11. <br/>
**Observations:** However, the instability of the short-term dynamics takes on the form of both motor stalling and loss of synchronism. <br/>

# Citation
This work comes from examples first presented in a MatLab Simulink model created and presented by T. Van Cutsem.


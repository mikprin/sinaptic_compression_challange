Фронт работ:

1. зарядка вне зависимости от ширины импульса
2. Более предсказуемое поведение при разрядке
3. Что делать если будет чтение в момент импульса


Постараться попасть до 10мс.



## Analog Circuit Design for Constant Charge Time in CMOS IC

To design an analog circuit for a CMOS IC where you aim to maintain a constant charge time for a current source (irrespective of pulse time) once a peak is detected, you can use a **Peak Detector and a Monostable Multivibrator (One-Shot Timer)** approach. Here's how this can be implemented:

### Circuit Breakdown

1. **Peak Detector Circuit**:
   - Use a **diode and capacitor-based peak detector** to capture the peak voltage of the input pulse. 
   - When the peak voltage of the pulse is reached, the capacitor holds the voltage, and this can trigger the next stage.

2. **Monostable Multivibrator (One-Shot Timer)**:
   - Use a **monostable multivibrator** circuit, typically based on an operational amplifier (op-amp) or a comparator, to generate a fixed-duration pulse.
   - The pulse time is set by an RC time constant, which is independent of the input pulse width, meaning it will only react when the peak detector reaches a certain threshold, and the monostable multivibrator will generate a constant output pulse.

3. **Current Source Control**:
   - The output of the monostable multivibrator can be used to enable a constant current source for a fixed duration.
   - The current source could be implemented using a **current mirror** circuit or a MOSFET-based design for controlling current flow.
   - The key is that the current source should be turned on for the duration of the monostable pulse, allowing a fixed charge to accumulate regardless of the pulse width or frequency of the input signal.

### Key Points to Ensure Constant Charge Time:

- The **RC time constant** of the monostable multivibrator defines the duration of the current source activation.
- Since the circuit is triggered by the peak detection, the charge time will remain constant, as the monostable multivibrator only resets after its set time.
- Ensure that your peak detection circuitry has a fast response time to avoid delays between the detection and the triggering of the one-shot timer.

### CMOS IC Considerations:

- For **CMOS integration**, use **MOSFETs** instead of BJTs for the current source and timing circuits to match the process technology.
- Low-power **CMOS comparators** or op-amps can be used in the peak detection and timing circuits.
- Ensure the use of **low-leakage capacitors** and **accurate resistors** in the RC circuit to maintain precise timing.

### Example Configuration

1. **Peak Detector:**
   - Input pulse -> Diode (for rectification) -> Capacitor (to hold the peak) -> Comparator to detect when the peak is reached.

2. **Monostable Circuit:**
   - Comparator output -> Monostable multivibrator (implemented with an RC network and an op-amp or a logic gate) -> Fixed pulse output.

3. **Current Source:**
   - Use a **PMOS/NMOS current mirror** to generate the desired constant current, controlled by the output of the monostable.

Would you like me to expand on the component-level details or simulation aspects of this design?
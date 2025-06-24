# CS-360-Mobile-Architect-Programming-2
CS 360 Programming
# CS-350 Portfolio: Emerging Systems Architectures & Technologies

This repository showcases two of my strongest CS 350 projects and a reflection on what I learned.

---

## ⚙️ Project Artifacts

1. **Thermostat Prototype**  
   - **Files**  
     - `main.py` — Python code implementing an OFF/HEATING/COOLING state machine with hardware-stub support  
     - `state_diagram.pdf` — Draw.io export of the thermostat state-machine diagram  
     - `reflection.docx` — Short reflection on the prototype and next-step recommendations  
   - **Highlights**  
     - Stubbed out GPIOZero, smbus2, and pyserial so that core logic runs on any desktop  
     - Pulsing LEDs, button-driven mode/temperature adjustment, console LCD simulation, comma-delimited UART messages

2. **Inventory SMS Notifier App**  
   - **Files**  
     - `MyLoginApp.zip` — Complete Android Studio project  
     - `LoginActivity.java` / `DatabaseActivity.java` — Login/registration + inventory CRUD + SMS notification code  
     - `state_machine.pdf` — (If you used a diagram here; otherwise omit)  
   - **Highlights**  
     - SQLite user table with registration & login  
     - RecyclerView grid of items + add/edit/delete dialogs  
     - Runtime SEND_SMS permission check; gracefully degrades if denied

> **Live repo:** https://github.com/your-username/cs350-portfolio  
> *(make sure your instructor is added as a collaborator so they can view these files)*

---

## 📝 Reflection

### 1. Project Summaries & Problems Solved  
- **Thermostat Prototype:**  Demonstrated state-machine logic for a three-state thermostat without access to actual hardware. Provided a desktop-testable stubbed implementation that can be retargeted to a Raspberry Pi or similar device.  
- **Inventory SMS Notifier:**  Addressed the need for persistent user management and CRUD inventory while handling Android’s runtime permissions for SMS alerts.  

### 2. What I Did Particularly Well  
- Modularized Python code: clear separation of sensing, actuation, UI simulation, and communication.  
- Correct use of Android’s runtime-permission API, with a flag to skip SMS calls if the user denies.  
- Produced a standards-compliant draw.io diagram and exported it as PDF.

### 3. Areas for Improvement  
- I stubbed hardware behavior heavily; I’d integrate real sensors/LEDs earlier in future iterations.  
- My Android string resources could be more complete (some hard-coded strings remain).  
- Unit tests are missing—adding `pytest`/`unittest` and JUnit would increase reliability.

### 4. Tools & Resources in My Support Network  
- **Python libs:** `gpiozero`, `smbus2`, `pyserial` for embedded prototyping  
- **Android Jetpack:** RecyclerView, Room (for future), and the Android Gradle Plugin Assistant  
- **Draw.io:** for quickly drafting state machines and UML diagrams  
- **GitHub Actions:** planned for CI linting and basic test runs

### 5. Transferable Skills  
- **State-machine design** for any finite-state process (UI flows, protocols)  
- **Dependency stubbing** to decouple logic from hardware, enabling desktop testing  
- **Graceful degradation**: handling user-denied permissions without breaking core functionality

### 6. Maintainability, Readability & Adaptability  
- **Descriptive naming** and **inline comments** clarify stub logic and timing decisions  
- **Configuration constants** at the top for pins, addresses, and intervals—easily swapped for real hardware  
- **Self-documenting draw.io PDF** accompanies code to speed up onboarding of new developers
## Reflection

**1. Summarize the project and what problem it was solving.**  
I built two key artifacts: (1) a **Thermostat Prototype** in Python that models a three-state (OFF/HEATING/COOLING) thermostat with stubbed GPIO, I²C, and UART interfaces, enabling desktop testing without real hardware; and (2) an **Inventory SMS Notifier Android app** featuring user registration/login, a SQLite-backed grid of items, and runtime SMS-permission checks to alert on low stock. Together these projects demonstrate end-to-end embedded control logic and a fully functional mobile CRUD + notification workflow.

**2. What did you do particularly well?**  
- **Modular design:** I separated sensing, actuation, display, and communication into clear methods (`read_temperature()`, `update_leds()`, `display_status()`, `send_uart_update()`), making logic easy to follow.  
- **Permission handling:** On Android, I correctly requested and handled SEND_SMS at runtime, gracefully degrading if denied.  
- **Hardware stubbing:** I wrapped all `gpiozero`, `smbus2`, and `pyserial` imports in `try/except` so the thermostat logic runs unmodified on any desktop OS.

**3. Where could you improve?**  
- **Unit testing:** I have no automated tests. Adding `pytest` or JUnit tests for state transitions and database operations would catch regressions early.  
- **Resource files:** The Android app still contains a few hard-coded strings; migrating all UI text into `strings.xml` would improve localization readiness.  
- **Real hardware integration:** I stubbed heavily—once I have hardware, I’ll replace stubs with live sensor/LED/button code and test on-device.

**4. What tools and/or resources are you adding to your support network?**  
- **Python libraries:** `gpiozero`, `smbus2`, and `pyserial` for on-device prototyping.  
- **Android Jetpack** components (e.g. Room for a more robust database layer).  
- **Draw.io** for diagrams, and **GitHub Actions** for future CI (linting/tests).  
- **Stack Overflow** and the official **Raspberry Pi documentation** for hardware-specific guidance.

**5. What skills from this project will be particularly transferable to other projects and/or coursework?**  
- **State-machine design**—applicable to any finite-state logic (protocols, UI flows, robotics).  
- **Dependency stubbing**—decoupling logic from hardware makes code portable and testable.  
- **Graceful degradation**—handling missing permissions or components without crashing.

**6. How did you make this project maintainable, readable, and adaptable?**  
- **Descriptive naming** (e.g. `toggle_mode()`, `increment_setpoint()`) and in-line comments clarify intent.  
- **Configuration constants** (pin numbers, I²C addresses, UART settings) at the top of each file allow quick re-targeting to new hardware.  
- **Single-source diagrams** (PDF-exported state machine) accompany code, so new developers can instantly grasp overall behavior.

---

Thanks for reviewing my work!  Please let me know if you have any questions or suggestions.  

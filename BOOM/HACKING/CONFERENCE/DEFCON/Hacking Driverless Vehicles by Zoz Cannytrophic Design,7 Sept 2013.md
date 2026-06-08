
### Summary of "Hacking Driverless Vehicles" by Zoz

Zoz, an expert in autonomous robots and unmanned systems, presents a comprehensive overview of the current state, vulnerabilities, and future challenges of **driverless vehicles and autonomous systems**. The talk is aimed at inspiring a security-minded approach to autonomous vehicle development, emphasizing the need to anticipate and address potential exploits before these technologies become deeply entrenched.

---

### Key Themes and Insights

- **Background and Motivation:**
    
    - Zoz’s experience spans autonomous ground and air vehicles, including UAVs (e.g., a life-saving beach drone) and driverless ground vehicles designed for tasks like high-speed pizza delivery.
    - Autonomous systems promise significant advantages: **energy efficiency**, **time efficiency**, elimination of human driver constraints (fatigue, rest stops), and enablement of new applications impractical with humans onboard.
    - The autonomous vehicle revolution is inevitable, and early discussion on security and vulnerabilities is crucial to guide safe and robust deployment.
- **Autonomy Spectrum:**
    
    - Unmanned does not always mean fully autonomous; some systems have off-board supervision or onboard safety pilots.
    - Military applications are leading adopters with classified capabilities focused on resistance to adversarial attacks.
    - Civil applications include transportation, oceanography, filmmaking, power line inspection, precision agriculture, and self-driving cars.
- **Challenges in the Civil Sphere:**
    
    - Shared infrastructure with humans complicates deployment.
    - Public acceptance hinges on **safety**, **robustness**, and **privacy**.
    - Failures often arise at the boundaries of designer expectations, as seen in historical UAV and autonomous vehicle test failures.
- **Behavioral Logic Hierarchy of Autonomous Systems:**
    
    - **Low-level control loops** ensure stability (e.g., flight control, balance).
    - **Collision avoidance** serves to protect the vehicle.
    - **Navigation and localization** manage route following.
    - **High-level mission planning** handles task execution.
    - Vulnerabilities increase when lower layers fail; attacking low-level functions can incapacitate the entire system.
    - Higher layers may be easier to exploit but often have fewer defenses.
- **Examples of System Vulnerabilities:**
    
    - UAV autopilot relying solely on GPS is vulnerable to GPS spoofing and jamming.
    - Pizza delivery robot’s collision avoidance and dynamic obstacle handling can be tricked by **redirection**, **trapping**, and **map confusion**.
    - Robots rely heavily on **sensor fusion and state estimation**, making them vulnerable to attacks that subvert or mislead perception.

---

### Sensor Attack Vectors and Exploits

|Sensor Type|Attack Type|Description / Effect|
|---|---|---|
|GPS|**Jamming and Spoofing**|Overpower satellite signals to deny or falsify location data; civilian GPS easily spoofed; military GPS more robust but not immune.|
|Laser Range Finder (LiDAR)|Denial (dust, smoke) & Spoofing|Interfering with return signals or manipulating surface reflectivity to produce false obstacle data.|
|Cameras|Blinding (dazzling), Spoofing|Vulnerable to bright light, camouflage, and confusing color patterns; used mainly for data colorization and object detection.|
|Millimeter Wave Radar|Chaffing, Reflectivity attacks|Lower resolution sensor; can be confused by reflective surfaces or spurious returns; used for collision avoidance.|
|Inertial Measurement Unit (IMU)|Hard to spoof but magnetic interference possible|Provides robust dead reckoning; cumulative error small but susceptible to magnetic fields.|
|Wheel Encoders|Physical damage or drift|Critical for speed and stop detection; damage or slippage causes localization errors or stoppage.|

- **Map Reliance:**
    - Extensive pre-mapped data (e.g., Google Maps) is treated as ground truth.
    - Changes in environment (e.g., moved traffic lights, overgrown vegetation) can cause robots to misinterpret or stop unnecessarily.
    - Attacks on map data via **denial-of-service**, **spoofing**, or **man-in-the-middle** can disrupt navigation and control.

---

### Logical and Physical Attack Strategies

- Increasing **state uncertainty** leads to mission failure.
- Fragile maneuvers such as right turns on red provide opportunities to confuse or trap vehicles.
- Physical proximity attacks (e.g., placing magnets near compasses) can disrupt sensors.
- Creating fake or modified obstacles can force robots to stop, reroute, or become trapped.
- Manipulating real-world infrastructure (e.g., traffic lights) or map data can cause robots to behave incorrectly.
- "Clobbering" attacks aim to force collisions or sensor damage.
- Subtle map or environment alterations near critical maneuvers can induce failures.

---

### Autonomous Vehicle Competitions and Opportunities for DEF CON Participants

- Zoz encourages **DEF CON hackers** to apply their skills constructively by participating in autonomous vehicle competitions:
    - **SAUC-E** – AUV waypoint navigation, object recognition, and Wi-Fi challenges.
    - **Roboboat** – Complex marine tasks including target identification, package retrieval, and multi-vehicle coordination.
    - **Robosub** – Underwater autonomy without GPS, involving navigation, object manipulation, and sonar pinger localization.
- Competitions reward innovative solutions in perception, navigation, and robustness.
- Opportunities exist for hacking rules, designing nontraditional vehicles, and exploring swarm autonomy.

---

### Conclusions and Final Remarks

- The driverless vehicle field is vibrant and rapidly evolving.
- **Security and robustness must be integral from the start**, embracing the hacking mindset to find and fix vulnerabilities.
- Physical and logical exploits are both realistic threats and valuable learning tools.
- Zoz urges hackers to contribute to building **safe, reliable, and innovative autonomous systems** rather than merely exploiting weaknesses.
- Autonomous vehicles promise to transform transportation, allowing humans to "get down to business in the back seat."


https://www.youtube.com/watch?v=n3i07GnOLO8


### Core Concepts and Background

- **NTLM (NT LAN Manager):**
    
    - A Windows authentication protocol used for password storage and network authentication.
    - Consists of LM (Lan Manager) and NTLM hashes:
        - **LM hash:** Splits password into two 7-character uppercase chunks, known to be weak and deprecated.
        - **NTLM hash:** Case-sensitive, stronger than LM but still vulnerable.
    - NTLM authentication involves a three-message challenge-response sequence:
        1. **Type 1:** Client sends supported authentication flags and domain/workstation info.
        2. **Type 2:** Server sends a unique challenge (to prevent replay attacks).
        3. **Type 3:** Client responds with the hashed challenge and credentials.
- **NTLMv2:**  
    Adds client-side randomness (client challenge) to mitigate rainbow table attacks.
    
- **Windows Integrated Authentication:**  
    Allows users on a domain to authenticate automatically to various services (network shares, internal web servers) without repeated password prompts.
    
    - Uses trusted security zones and "one-word" domain names (e.g., intranet names) to determine authentication scope.
    - Network broadcasts such as NBT-NS and SMB allow automatic authentication without explicit user interaction.

---

### NTLM Relaying vs. Pass-the-Hash

- **Pass-the-Hash (PtH):**
    
    - Requires access to password hashes on the local system or memory (usually local admin privileges).
    - Involves replaying captured hashes to authenticate elsewhere.
- **NTLM Relaying:**
    
    - Does **not** require prior credentials or system access.
    - Attacker sets up a rogue server to intercept and relay authentication requests to legitimate servers, exploiting the lack of host verification in NTLM protocol.
    - Can start from network connectivity only, even as a guest.

---

### Historical Timeline of NTLM Relaying Research

|Year|Event/Research Highlight|
|---|---|
|1996|Dominique's paper on weaknesses in NTLM authentication introduced relaying concept.|
|2000|Dildog's SMB relay tool demonstrated NTLM relaying in practice.|
|2008|Microsoft patch (MS08-068) mitigated NTLM relay attacks bouncing back to self but not to other hosts.|
|2008|Grutz's Defcon talk “NTLM is Dead” highlighted NTLM relaying over HTTP and SMB.|
|2010|FireSheep demonstrated ease of session hijacking over HTTP, inspiring similar ease-of-use tool for NTLM relaying.|

---

### The Zack Attack Tool: Features and Innovations

- **Motivation:**  
    Existing tools for NTLM relaying are limited to SMB and HTTP protocols and forward all authentication requests to a single noisy target.
    
- **Key Improvements:**
    
    - Supports **cross-protocol NTLM relaying** including SMB, HTTP, LDAP, MSSQL, Remote Desktop, VPNs, and Exchange Web Services (EWS).
    - Allows **targeted relaying** based on user identity and group membership with rule-based automation (e.g., escalate privileges on domain admins automatically).
    - Maintains **persistent authentication sessions** by forcing users to reauthenticate without disconnecting to maximize exploitation.
    - Provides multiple **payload generation methods** to coerce clients to authenticate automatically (e.g., WPAD spoofing, UNC paths in browsers, QuickTime playlists, Outlook HTML emails, desktop.ini files).
    - Offers a **RESTful API** for integration with custom tools.
- **How it Works:**
    
    - Sets up rogue HTTP and SMB servers to capture NTLM authentication requests.
    - Uses a custom "Alzheimer feature" that forgets user identity post-authentication and forces reauthentication to identify users dynamically.
    - Uses session keep-alive techniques (e.g., HTTP 302 redirects with keep-alive) to maintain connections.
- **Payload Delivery Techniques:**
    
    - **WPAD (Web Proxy Auto-Discovery):** Spoofs WPAD requests to induce automatic authentication.
    - **Browser Techniques:** Previously, Firefox and Chrome blocked automatic SMB authentication; Zack Attack circumvents this by forcing file downloads or leveraging plugins like QuickTime to trigger network authentication.
    - **Email and Office Suite:** Embeds UNC paths in HTML emails or Office documents to trigger automatic authentication.
    - **Desktop.ini and .lnk files:** Exploits Windows features to automatically authenticate when folders or shortcuts are accessed.




# SecureVault Password Manager

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white) ![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black) ![CryptoJS](https://img.shields.io/badge/CryptoJS-Encryption-blue?style=for-the-badge)

SecureVault is an enhanced client-side password manager that allows you to securely store your passwords, generate strong random passwords, and organize your credentials. All data is encrypted and stored locally in your web browser's `localStorage`.


## New Features in this Version!

* **Password Categories & Tags:** Organize passwords with predefined categories and custom tags.
* **Filtering:** Easily filter stored passwords by category and tags.
* **Auto-Logout:** Automatically locks the vault after a period of inactivity (5 minutes).
* **Favicon Display:** Shows website favicons for easier identification.
* **Password Expiry Warning:** Notifies you if a password hasn't been updated in over 90 days.
* **Biometric Authentication (Experimental):** Option to use platform biometric authentication (fingerprint, face recognition via WebAuthn API if supported by browser/device) after initial master key setup.
* **Enhanced UI:** Improved layout and visual cues, including password strength for manually entered passwords in the modal.

## Core Features

* **Master Key Authentication:** Secure your vault with a master key.
* **Secure Password Storage:** Passwords are encrypted using AES (Advanced Encryption Standard) via CryptoJS.
* **Password Generation:**
    * Configurable password length (8-32 characters).
    * Options to include uppercase letters, lowercase letters, numbers, and symbols.
    * Password strength meter.
* **Clipboard Functionality:** Easily copy generated or stored passwords.
* **Stored Password Management:** View/Hide, Add, Delete credentials.
* **Client-Side Operation:** Runs entirely in your browser. No data is sent to any server.
* **Responsive Design:** Adapts to different screen sizes (thanks to Tailwind CSS).

## Technologies Used

* **HTML5:** For the application structure.
* **Tailwind CSS:** For styling (loaded via CDN).
* **JavaScript (ES6+):** For all application logic and interactions.
* **Font Awesome:** For icons (loaded via CDN).
* **CryptoJS:** For client-side AES encryption and SHA256 hashing (loaded via CDN).
* **Web Authentication API (WebAuthn):** For experimental biometric authentication.

## How to Use / Setup

1.  **Download or Clone:**
    * Download the `index.html` file.
    * OR Clone the repository: `git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git`
2.  **Open in Browser:**
    * Navigate to the project directory.
    * Open the `index.html` file in a modern web browser (e.g., Chrome, Firefox, Edge).
3.  **Master Key Setup:**
    * On your first visit, you will be prompted to enter and set a Master Key. **Choose a strong, unique master key and remember it! This key is used to encrypt and decrypt your passwords. If you forget it, you will lose access to your stored passwords.**
    * On subsequent visits, enter the same Master Key to unlock your vault. You may also see an option for biometric authentication if your browser/device supports it and you've previously linked it.

## Project Structure

The project is a single `index.html` file which includes:
* HTML markup for the user interface.
* Inline CSS styles and Tailwind CSS classes (Tailwind is loaded from a CDN).
* All JavaScript logic for the application's functionality.
* CryptoJS and Font Awesome are also loaded from CDNs.

## How It Works (Technical Overview)

* **Master Key:**
    * The SHA256 hash of your master key is stored in `localStorage` for verification.
    * The raw master key (in a JavaScript variable during session) is used for AES encryption/decryption.
* **Password Storage & Encryption:**
    * Password entries are stored as an array of objects. Each object includes `website`, `username`, `password`, `category`, `tags` (as a comma-separated string), and `lastUpdated` timestamp.
    * This array is JSON stringified, then AES encrypted with the master key, and stored in `localStorage`.
* **Inactivity Logout:** A timer resets on user activity (mouse, keyboard). If inactive for 5 minutes, the vault locks, clearing the master key from memory.
* **Biometric Authentication (Experimental):**
    * Leverages the WebAuthn API (`navigator.credentials.get`).
    * This feature is for unlocking an already set up vault and currently requires an initial master key entry to associate the biometric credential with the vault for simplicity in this client-side model. Its availability depends on browser and platform support for user-verifying platform authenticators.
* **Favicons:** Fetched using `https://www.google.com/s2/favicons?domain=<website_domain>`.

## ⚠️ Security Disclaimer ⚠️

* **Client-Side Only:** All data is stored locally in your browser's `localStorage`.
* **Master Key Strength:** The security hinges on your Master Key's strength and secrecy.
* **Device Security:** If your device/browser is compromised, `localStorage` could be accessed.
* **Not Formally Audited:** This is an educational project and has not undergone formal security audits.
* **XSS Risk:** Be cautious of XSS vulnerabilities if the page context was ever compromised.
* **Biometric Feature:** The biometric authentication is experimental and relies on browser/platform capabilities and security. It does not replace the need for a strong master key, as the master key is still fundamental to the encryption process.
* **Use with Caution:** Use thoughtfully, especially for highly sensitive accounts. Consider professionally audited managers for critical needs.
* **Backup:** No automatic backup. Data is in `localStorage` only. Clearing browser data for this site will erase passwords.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

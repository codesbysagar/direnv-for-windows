# Setting Up Direnv on Windows

This guide explains how to set up and use `direnv` on a Windows system, particularly with Git Bash, for managing project-specific environment variables. 🚀

---

## **Prerequisites**
- 🖥️ Windows operating system
- 🛠️ Git Bash installed

---

## **Steps to Set Up Direnv**

### 1. **Download Direnv** 📥
1. Visit the [Direnv releases page](https://github.com/direnv/direnv/releases).
2. Download the latest `direnv.windows-amd64.exe` binary.
3. Rename the downloaded file to `direnv.exe`.
4. Place the file in a directory, such as `C:/tools/direnv/`.
   > ⚠️ *It is not mandatory to have the same directory structure, just make sure you want PATH for the directory to add in SYSTEM ENVIRNMENT VARIABLES.*

---

### 2. **Add Direnv to System PATH** 🔗

1. Open **Environment Variables**:
      - Press `Win + S` and search for `Environment Variables`. 
      - Click on **Edit the system environment variables**.
2. Under **System Variables**:
      - Select the `Path` variable and click **Edit**. 
      - This opens a list of paths.
3. Add the path to the directory containing direnv.exe:
      - For example, `C:/tools/direnv/`. 
      - Click **New** and paste the path.
4. Click **OK** to save.
      - Close all dialogs.

## Screenshots
<img src="https://github.com/codesbysagar/direnv-for-windows/blob/main/direnvScreenshots/step1.png" alt="Step1" height="200">
<img src="https://github.com/codesbysagar/direnv-for-windows/blob/main/direnvScreenshots/step2.png" alt="Step2" height="200">
<img src="https://github.com/codesbysagar/direnv-for-windows/blob/main/direnvScreenshots/step3.png" alt="Step3" height="200">
<img src="https://github.com/codesbysagar/direnv-for-windows/blob/main/direnvScreenshots/step4.png" alt="Step4" height="200">
---

### 3. **Verify Direnv Installation** ✅
(It will a good to restart you PC to make sure the direnv is added successfully to *system environment variables*)

1. Open Git Bash:
2. Run the following command:
```bash
direnv version
```  
You should see the installed version of `direnv`.

---

### 4. **Integrate Direnv with Git Bash** 🖇️(*run the below commands in bash*)
1. Open the ~/.bashrc file:
   ```bash
   nano ~/.bashrc
   ```
   *(If you prefer another editor, use that instead like vim etc.)*

2. Add the following line at the end of the file:
   ```bash
   eval "$(direnv hook bash)"
   ```

3. Save and exit the editor.

4. Reload the `.bashrc` file:
   ```bash
   source ~/.bashrc
   ```

---

### 5. **Create a Project with `.envrc`** 🗂️
1. Navigate to your project directory:
   ```bash
   cd /path/to/your/project
   ```

2. Create a `.envrc` file:
3. Add the env you want to use in below pattern:
   ```bash
   export <Key>="<Value>"
   ```
- example:
```bash
export MONGO_URI="Connection String"
```
4. Allow the `.envrc` file with below `bash` command:
   ```bash
   direnv allow
   ```

5. Now, whenever you enter this directory:
   - `direnv` will automatically load the environment variables. 🌟

---

### 6. **Optional: Add `.envrc` to `.gitignore`** 🚫
Prevent the `.envrc` file from being tracked by Git:
Inside the `.gitignore` add `.envrc` and `git` will exclude that `.envrc`
### **Why Add `.envrc` to `.gitignore`?** 🛡️

#### **Protect Sensitive Data** 🔒  
`.envrc` files often contain sensitive information like API keys, database credentials, or other configuration details specific to your local environment. Sharing these unintentionally could expose your system to security risks.

#### **Prevent Configuration Conflicts** ⚙️  
Environment settings in `.envrc` are often tailored to individual machines. Pushing this file to a repository could overwrite or conflict with others' configurations, leading to unnecessary debugging and errors.

#### **Encourage Local Customization** 🧩  
By ignoring `.envrc`, each developer can customize their local environment without worrying about syncing these changes with the repository, fostering flexibility and independence.

#### **Reduce Risk of Accidental Commits** 🚫  
It's easy to forget that a `.envrc` file contains sensitive data. Adding it to `.gitignore` eliminates the risk of accidentally committing and exposing critical information.


---

## **Common Commands** 📜
| Command            | Description                                           |
|--------------------|-------------------------------------------------------|
| `direnv allow`     | Approve the `.envrc` file in the current directory.   |
| `direnv deny`      | Disallow the `.envrc` file in the current directory.  |
| `direnv reload`    | Reload the `.envrc` file.                            |
| `direnv version`   | Check the installed version of `direnv`.             |

---

## **Troubleshooting** 🛠️

### Problem: `direnv: command not found`
- Ensure `direnv.exe` is added to the PATH.
- Verify the PATH changes by restarting Git Bash and running:
  ```bash
  echo $PATH
  ```

### Problem: `.envrc is blocked`
- Run `direnv allow` to approve the `.envrc` file.

### Problem: Changes to `.envrc` are not applied
- Run `direnv reload` to apply updates to the `.envrc` file.

---

You’re now set up to use `direnv` for managing project-specific environment variables on a Windows system! 🎉

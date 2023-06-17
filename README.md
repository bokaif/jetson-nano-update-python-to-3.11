# Upgrading Python on Jetson Nano to 3.11

Follow these steps to upgrade Python on your Jetson Nano from version to 3.11 and make it the default `python3` version.

1. **Backup**: Before starting, ensure you have a backup of any important files or projects in your current Python environment.

2. **Update system packages**:
   ```shell
   sudo apt update
   sudo apt upgrade
   ```

3. **Install prerequisites**:
   ```shell
   sudo apt install build-essential libssl-dev zlib1g-dev libncurses5-dev libncursesw5-dev libreadline-dev libsqlite3-dev libgdbm-dev libdb5.3-dev libbz2-dev libexpat1-dev liblzma-dev libffi-dev
   ```

4. **Download Python 3.11 source code**: 
   - Obtain the latest release from the official [Python website](https://www.python.org/downloads/), or
   - Use the following commands to download and extract the source code:
     ```shell
     wget https://www.python.org/ftp/python/3.11.0/Python-3.11.0.tar.xz
     tar -xf Python-3.11.0.tar.xz
     ```

5. **Navigate to Python source code directory**:
   ```shell
   cd Python-3.11.0
   ```

6. **Configure the build process**:
   ```shell
   ./configure --enable-optimizations
   ```

7. **Start the build process**:
   ```shell
   make -j$(nproc)
   ```

8. **Install Python 3.11**:
   ```shell
   sudo make altinstall
   ```

9. **Verify installation**:
   ```shell
   python3.11 --version
   ```

10. **Update pip**:
    ```shell
    python3.11 -m pip install --upgrade pip
    ```

11. **Make Python 3.11 the default**:
    - Backup the existing `python3` symlink:
      ```shell
      sudo mv /usr/bin/python3 /usr/bin/python3_backup
      ```
    - Create a new symlink to Python 3.11:
      ```shell
      sudo ln -s /usr/local/bin/python3.11 /usr/bin/python3
      ```

12. **Verify default Python version**:
    ```shell
    python3 --version
    ```

    The output should display the Python 3.11 version.

Note: Remember to update any virtual environments or project configurations that rely on Python to use the new version as well.


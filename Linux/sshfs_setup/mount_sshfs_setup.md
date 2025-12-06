# SSHFS Setup

Setup to mount files from Beluga (or other) locally. Useful when in need to use local tools like IGV.

### Tested on macOS Sonoma 14.6

1. **Install macFUSE**
    
    macFUSE allows you to extend macOS's native file handling capabilities via third-party file systems. 
    
    You may need to restart your system after this step.
    
    <u>With Homebrew <u>
    
    ```bash
    brew install --cask macfuse
    ```
    

	 <u>Without Homebrew <u>

	Visit macFUSE’s website. Download the macFUSE .pkg file. Open and follow the instructions.

	![image.png](macfuse_pkg.png)

1. **Install SSHFS**
    
    SSHFS (SSH Filesystem) is a filesystem client to mount and interact with directories and files 
    located on a remote server or workstation over a normal ssh connection.
    
    <u>With Homebrew<u>
    
    ```bash
    brew install gromgit/fuse/sshfs-mac
    
    # Verify installation
    sshfs --version
    ```
    
    <u>Without Homebrew<u>
    
    Visit macFUSE’s website. Download the SSHFS .pkg file. Open and follow the instructions.
    
    ![image.png](sshfs_pkg.png)
    
2. **Enable system extensions in Recovery environment (for Apple Silicon)**
    
    Shut down your system. 
    
    Press and hold the power button to launch Startup Security Utility.
    
    Select Options.
    
    Log into an admin user.
    
    In upper toolbar, go in Utilities and select Startup Security Utility.
    
    Select your system and click Security Policy (lower right).
    
    Select Reduced Security and tick Allow user management of kernel extensions from identified developers.
    
    Restart your system.
    
3. **Create a local mount directory**
    
    Any directory you want to access the structure from.
    
    ```bash
    mkdir /path/to/local/mount
    ```
    
4. **Mount the Remote Filesystem**
    
    When mounting for the first time, make sure to Allow the use of macFUSE in Privacy and Security settings (will pop up).
    
    ```bash
    sshfs youruser@desiredserver:/path/to/desired/directory /path/to/local/mount -o volname=mount
    ```
    
    Where *mount* is the name of the local directory you’re using.
    
    For example:
    
    ```bash
    sshfs ccharest@beluga.computecanada.ca:/project/6019267 /Users/cosmic/Documents/beluga -o volname=beluga
    ```
    
5. **Unmount the Remote Filesystem**
    
    When you’ve finished using the mount:
    
    - Ensure you are not currently inside the mounted directory in any terminal session.
    - Close any applications or file browsers that might be accessing the mounted directory.
    
    ```bash
    umount /path/to/local/mount
    ```
    

### For Windows

Haven’t tried it but this tutorial seems exhaustive: [https://www.petergirnus.com/blog/how-to-sshfs-on-windows](https://www.petergirnus.com/blog/how-to-sshfs-on-windows)

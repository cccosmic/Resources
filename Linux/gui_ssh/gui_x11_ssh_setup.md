# Use Graphical Applications via the X11 protocol with SSH

Author: Carolane Charest

Date: December 4th, 2025

What is X11? [https://www.baeldung.com/linux/x11](https://www.baeldung.com/linux/x11)

MacOS

1. **Install the software to support X11**
    - XQuartz is an open-source version of the [X.Org](http://x.org/) X server, a display server for the X Window System that runs on macOS.
    - After installation, open XQuartz.
    
    With brew:
    
    ```bash
    brew install --cask xquartz
    ```
    
    From Web: [https://www.xquartz.org/](https://www.xquartz.org/)
    
2. **Connect to the HPC with SSH.**
    - -Y allows for X11 communications
    - As suggested in *X11 for Graphical Applications* in [https://docs.alliancecan.ca/wiki/SSH](https://docs.alliancecan.ca/wiki/SSH)
    
    ```bash
    ssh -Y username@cluster_name
    ```
    

1. **Start the interactive job with X11 flag.**
    - Should pop up GUIs in your local machine when using relevant commands
    - Based on *Interactive Jobs* Section in [https://docs.alliancecan.ca/wiki/Running_jobs](https://docs.alliancecan.ca/wiki/Running_jobs)
    
    ```bash
    salloc --x11 --time=1:0:0 --mem-per-cpu-3G --ntasks=1 --account=rrg-tetreaum
    # ... do your thing 
    # you can try running the command "xclock"
    exit # when done working
    ```
    

1. **Close the XQuartz software.**
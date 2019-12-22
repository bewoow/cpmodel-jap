# "Heart-lung interactions during mechanical ventilation: Analysis via a cardiopulmonary simulation model" - Karamolegkos, Albanese, Chbat
## Journal of Applied Physiology

### Requirements:
  * Matlab R2017b or newer (with Simulink installed)
  * Windows or Mac (both 64bit)

### Files
1. **R2019a** folder 
  * *cpm_jap_R2019a.slx* : Main Simulink file for Matlab R2019a or newer (please note the "R2017b" files can be used for all Matlab versions beyond R2015b, but it's recommended to use the newer version for better compatibility)
  * *CP_sf.mexw64* : Compiled code of the modified CP Model (for Windows; for the R2019a main file)
  * *CP_sf.mexmaci64* : Compiled code of the modified CP Model (for MacOS; for the R2019a main file)
2. **R2017b** folder -> To Be Checked
  * *cpm_jap_R2017b.slx* : Main Simulink file for Matlab R2017b, R2018a, R2018b
  * *CP_sf.mexw64* : Compiled code of the modified CP Model (for Windows; for the R2017b main file)
  * *CP_sf.mexmaci64* : Compiled code of the modified CP Model (for MacOS; for the R2017b main file)

Practically, the "slx" files are the main files that one needs to open for starting the model simulation, for changing the model parameters, as well as for plotting purposes. The "mex" files contain the compiled code of the dynamic equations of the modified CP Model. Please note that the user only interacts with the "slx" file as per the instructions below.

### Instructions
1. Download all model-related supplement files (as included in the above “Files” list and based on the installed Matlab version) to the desired directory.
2. Navigate to the directory that contains the downloaded files and open the "slx" file. Matlab is expected to open and you will see the following window to appear (if this does not work, please open Matlab first, navigate to the directory with the files, and then open the "slx" file via Matlab):
![alt text](https://github.com/bewoow/cpmodel-jap/blob/master/images/slx_main_file.png)
3. The single visible Simulink block, named *CP Model*, provides an easy access to model parameters, allowing the user to change their values. The parameters are categorized in the modified CP Model's main compartments, i.e., heart, lungs, circulation, neural feedback, metabolism, and gas exchange. The CP Model's default parameter values have been pre-configured and are always selected at the model's initialization phase.
4. For plotting, please consider adding scopes in the place of the Ground block, right after the Bus Selector block. The purpose of the Bus Selector block (black vertical line in the above figure) is to allow selection of the desired signals (model variables) for plotting. Double-clicking on it reveals a window (see below) where the desired signals can be selected by dragging them from the left (named “Signals in the bus”) to the right (named “Selected signals”) panel (for reference, Psa has been pre-selected). The signals have been categorized similar to the parameters above. Adding a new signal on the right panel creates a new output of the Bus Selector block that can then be connected to a Scope input. Notice that, for reference, the variables’ units have also been included in the corresponding signal’s name.
![alt text](https://github.com/bewoow/cpmodel-jap/blob/master/images/bus_selector.png)
5. Simulation can be started by clicking on the play button at the toolbar after selecting the desired simulation time (default is infinity, i.e., until the user clicks stop).
6. During the simulation time, the user can double-click on the “CP Model” block and change the desired parameter value(s). If, for example, a change in lungs compliance (CL) is to be considered, the user should click on the “Lungs” tab and adjust the corresponding parameter (see screenshot below) from its nominal (default; 0.2 l/cmH2O in this case) value to the desired one.
![alt text](https://github.com/bewoow/cpmodel-jap/blob/master/images/lungs_parameters.png)
7. Upon ending the simulation execution, a structure variable named “cpmResults” will be saved at Matlab’s workspace. It follows the same arrangement as the one of the Bus Selector. Saving the model’s outputs can then be readily performed by saving the “cpmResults” structure file (right click on the file on Matlab’s workspace and then select “Save As” to the desired directory).
8. Further data processing can be conducted either via Matlab’s commands or via the Simulation Data Inspector (for easy graphical representation of model’s outputs; see more information at https://www.mathworks.com/help/simulink/ug/simulation-data-inspector-overview.html).

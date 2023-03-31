
Use [VeriStand Model Generation Support](./Home) to create VeriStand
compatible models within the MathWorks Simulink® environment.

Before you begin, [install all required software](./Installation-Guide) and
ensure you are running [supported versions of MATLAB and
Simulink](./Compatibility-Considerations).

1. Open a model in the Simulink Editor.
2. Click **Model Settings** » **Model configuration parameters**.
3. In the Configuration Parameters: Configuration window, click **Code
    Generation** and set the **System target file** to `veristand.tlc`.
4. In the **Toolchain** drop-down box, select the VeriStand toolchain based on the destination target.

      | Target         |   Toolchain                                                                              | Device vendor |  Device type      |
      |--------------- | ---------------------------------------------------------------------------------------- | ------------- | ----------------- |
      | Windows        |   GCC Compiler for VeriStand Windows targets \| gmake makefile (64-bit Windows)          |    Intel/AMD  | x86-64 (Windows64)|
      |Linux Real-Time | GCC Compiler for VeriStand NI Linux Real-Time targets \| gmake makefile (64-bit Windows) |  Intel        |  x86-64 (Linux 64)|

5. Under **Hardware Implementation** set the compatible device type and
    device vendor.
6. **(Optional)** Enable Signals to be exported. Under **Code Generation** » **Interface** enable the **Signals** checkbox and designate the required signals on the block diagram as **Test Point**.
7. **(Optional)** Enable External Mode. Refer to [External
    Mode](./External-Mode) section for more details.
8. **(Optional)** Update other model configuration settings.
9. Click **OK**.
10. Build the model.

Once built, the `.vsmodel` file will appear in the code generation folder. This model can be imported into a VeriStand system definition and deployed to Windows and NI Linux Real-Time systems.

**Note**: VeriStand Model Generation Support does not provide an API.

NI supports VeriStand Model Generation Support. For issues related to
this add-on, visit [www.ni.com/ask](https://www.ni.com/ask) to open a
service request or file a bug report.


# Lab 1 File Add Instructions
1. Download everything in `lab1/` from [AAML2026-Lab](https://github.com/nycu-caslab/AAML-Labs-2026).
2. Replace existing files or add new files to `Platform/sw/project/` using the downloaded version.
3. Add the following line to `project.mk`:
   ```make
   APP_EXTRA_SRCS += $(wildcard models/label/label*_board.cc)
   ```
   Alternatively, you can define `APP_EXTRA_SRCS` when running `make`.
4. From the repository root, run the following preflight checks **before editing the RTL**:
   ```bash
   vivado -version
   verilator --version
   c++ --version
   riscv64-unknown-elf-g++ --version
   python3 -c "import serial"
   make -C Platform/sw validate

   make -C Platform/sw check-env \
     MODEL_FILE=ds_cnn_stream_fe.tflite \
     MODEL_PROFILE=ds_cnn_stream_fe
   ```

These checks ensure that the required tools, compiler, Python dependencies, and project environment are correctly configured before starting the lab.

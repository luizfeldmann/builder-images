FROM mcr.microsoft.com/windows/servercore:ltsc2022

# The CMD shell
SHELL ["cmd", "/S", "/C"]

# Install Chocolatey
RUN powershell.exe -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command \
    "[System.Net.ServicePointManager]::SecurityProtocol = 3072; \
    iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))"

# Install utils
RUN choco install -y \
        git \
        ninja \
        jq \
        7zip

RUN choco install -y cmake --version=3.31.12
RUN choco install -y python --version=3.12.10

# Install build tools
RUN choco install -y visualstudio2022buildtools
RUN choco install -y visualstudio2022-workload-vctools \
    --package-parameters "--no-includeRecommended --add Microsoft.VisualStudio.Component.VC.Tools.x86.x64"

# NOTE: check component names here: https://learn.microsoft.com/en-us/visualstudio/install/workload-component-id-vs-build-tools?view=vs-2022

# Install Conan
RUN python -m pip install --no-cache-dir "conan==2.30.0"
RUN conan profile detect --force

WORKDIR /workspace

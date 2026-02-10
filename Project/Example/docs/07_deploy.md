# Deployment / Packaging

## 1. What “deployment” means for this project
- Option A: Provide a release binary
- Option B: Provide a Docker image to run the CLI

## 2. Build Instructions
- cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
- cmake --build build

## 3. Run Instructions
- Example command(s):

## 4. Docker (if used)
- Build: docker build -t <name>:<tag> .
- Run: docker run --rm -v "$PWD:/work" <name>:<tag> <command>

## 5. Versioning
- Tag format: vMAJOR.MINOR.PATCH
- Update CHANGELOG.md for each tag

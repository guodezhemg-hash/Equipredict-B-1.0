# Equipredict-B-1.0
# Docker Usage

The Docker image archive can be downloaded from Baidu Netdisk:

Link: https://pan.baidu.com/s/1cJZtEH-6RZUBx2WNiOJyqg?pwd=htj4
File name: equipredict-b:1.0.tar.gz
Docker image tag after loading: equipredict-b:1.0

The SHA256 checksum of the Docker image archive is provided in checksums.txt.

## Load The Offline Image

```powershell
docker load -i "equipredict-b_1.0.tar"
```

## Run And Output To Current Folder

PowerShell:

```powershell
docker run --rm -v "${PWD}:/app/output" equipredict-b:1.0
```

Command Prompt:

```cmd
docker run --rm -v "%cd%:/app/output" equipredict-b:1.0
```

After the run finishes, the result file will be in the current folder:

```text
baijiu_equilibrium_results.xlsx
```

## Run With Custom Input Excel Files

Put your files in one folder, for example:

```text
D:\mydata\model.xlsx
D:\mydata\concentration.xlsx
```

Then run:

```powershell
docker run --rm `
  -v "D:\mydata:/data" `
  -v "${PWD}:/app/output" `
  -e MODEL_PATH="/data/model.xlsx" `
  -e CONC_PATH="/data/concentration.xlsx" `
  equipredict-b:1.0
```

## Build The Image

Run this command in the project folder:

```powershell
docker build -t equipredict-b:1.0 .
```

## Export The Offline Image

```powershell
docker save -o equipredict-b_1.0.tar equipredict-b:1.0
```

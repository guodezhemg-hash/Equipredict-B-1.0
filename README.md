# Equipredict-B-1.0
# Docker Usage

This image runs the Baijiu equilibrium calculation once, then writes the Excel result to `/app/output` inside the container.

To see the output on your computer, mount a host folder to `/app/output`.

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
D:\mydata\conceration.xlsx
```

Then run:

```powershell
docker run --rm `
  -v "D:\mydata:/data" `
  -v "${PWD}:/app/output" `
  -e MODEL_PATH="/data/model.xlsx" `
  -e CONC_PATH="/data/conceration.xlsx" `
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

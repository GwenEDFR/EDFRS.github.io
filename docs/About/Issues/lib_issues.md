# Kaleido image export issues

When export issues with pio.to\_image only.\
If no file is created or your code run in void, you'll need this .whl to fixed the engine kaleido. This issue is only for windows laptop, mac and linux don't have this issue.

1. Download the file **kaleido-0.1.0.post1-py2.py3-none-win\_amd64.whl** (for windows 10 in amd 64). You can download it [here](https://github.com/plotly/Kaleido/releases/tag/v0.1.0.post1)
2. Copy the file in your name\_of\_venv folder and switch into it (`cd name_of_venv`)\

3. Install this librarie in your venv

```
pip install --trusted-host pypi.org --trusted-host files.pythonhosted.org -U kaleido-0.1.0.post1-py2.py3-none-win_amd64.whl
```

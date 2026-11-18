# Hoffman2 Jupyter smoke test

Mac instructions
 copy the notebook to your Hoffman2 home directory. Replace `YOUR_HOFFMAN2_USERNAME` with your cluster username.

```sh
hoffman2_user=YOUR_HOFFMAN2_USERNAME
scp hoffman2-smoke-test.ipynb "${hoffman2_user}@hoffman2.oarc.ucla.edu:~/"
```

In the same local terminal, download the launcher linked by UCLA and start a Jupyter session on a Hoffman2 compute node.

```sh
launcher_dir=$(mktemp -d)
curl -fL https://raw.githubusercontent.com/rdauria/jupyter-notebook/main/h2jupynb_slurm \
  -o "${launcher_dir}/h2jupynb" &&
  python3 "${launcher_dir}/h2jupynb" -u "$hoffman2_user"
```

When Jupyter opens in your browser, open `hoffman2-smoke-test.ipynb` and run its code cell. Save any changes and press **Ctrl+C** in the launcher terminal to end the Slurm session.

Jupyter saves edits on Hoffman2. To bring them back to this repository, run the following from the repo directory after saving the remote notebook. This replaces the local copy with the remote copy. Clear notebook outputs before committing if they contain cluster details.

```sh
scp "${hoffman2_user}@hoffman2.oarc.ucla.edu:~/hoffman2-smoke-test.ipynb" .
```

[UCLA Hoffman2 connection guide](https://www.hoffman2.idre.ucla.edu/Using-H2/Connecting/Connecting.html)

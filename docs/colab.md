# Google Colab and GPU workflow

Use Colab only when the workload benefits from a remote GPU or TPU. Keep VS Code and the local Git repository as the editing and review workspace.

## Recommended flow

1. Edit and test lightweight code locally in VS Code.
2. Commit the coherent change to a task branch and push it to GitHub.
3. Open `notebooks/colab_gpu_check.ipynb` from GitHub in Google Colab.
4. In Colab, choose **Runtime > Change runtime type** and select a GPU only when the workload needs one.
5. Run the environment-check cells before a training or numerical workload.
6. Record the branch, commit, Python and framework versions, accelerator, configuration, and random seed with important results.
7. Save code and small configuration files in GitHub. Store datasets, checkpoints, and large outputs outside Git.

Colab runtimes are temporary and their GPU model is not guaranteed. A GPU runtime also does not guarantee that a workload actually uses the GPU.

## Open the smoke-test notebook

After this branch is pushed, use:

```text
https://colab.research.google.com/github/nfukulab7/git-practice/blob/chore/development-environment/notebooks/colab_gpu_check.ipynb
```

After a human merges the Pull Request, replace the branch segment with `main`.

## Files and authentication

The local Windows filesystem and Colab's `/content` filesystem are separate.

- Use GitHub clone or the Colab GitHub notebook loader for code.
- Use Google Drive or project-specific cloud storage for large data and outputs.
- Complete Google or GitHub authentication only through the official human-controlled flow.
- Never paste passwords, tokens, or Drive credentials into source code or notebooks.
- Never commit `.env` files, datasets, checkpoints, or generated training outputs.

Example public-repository checkout inside Colab:

```python
!git clone --branch main --depth 1 https://github.com/nfukulab7/git-practice.git
%cd git-practice
```

For a private repository, do not place a personal access token in the notebook. Use an approved authentication mechanism and keep secrets outside saved notebook cells.

## Reproducibility checklist

Record these values for meaningful runs:

- Git repository, branch, and commit hash
- Python and framework versions
- dependency lock or environment file
- dataset version or immutable location
- model and experiment configuration
- random seed
- accelerator type and relevant CUDA version
- output location

Run lightweight unit tests locally and in CI. Reserve Colab for accelerator validation, notebook smoke tests, and workloads that are impractical on the local machine.

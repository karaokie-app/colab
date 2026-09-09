# karaokie worker, on a borrowed GPU

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/karaokie-app/colab/blob/main/karaokie_worker.ipynb)

[karaokie.app](https://karaokie.app) turns any song into a karaoke track:
the voice separated from the music, and every word of the lyrics placed
against it. That is a few minutes of work for a graphics card, and it is done
by whoever lends one — not by the small machine that serves the site.

This repository holds one notebook. It borrows the graphics card Google Colab
gives a browser tab, puts it on the queue, and hands the finished songs back.
Nothing is installed on your own machine and there is no account to make.

**[Open the notebook in Colab](https://colab.research.google.com/github/karaokie-app/colab/blob/main/karaokie_worker.ipynb)**,
choose **T4 GPU** under Runtime ▸ Change runtime type, and run the two cells.

The first cell checks the two things Colab is inconsistent about: whether the
runtime really did get a card, and whether YouTube will answer this machine at
all — datacentre addresses are the ones asked to prove they are not a robot.
The second downloads the worker, checks it against its published SHA-256, and
runs it.

Stop it whenever you like. A song caught half-done is a lease that stops being
renewed, and goes back on the queue for the next worker a few minutes later.

## What it actually runs

The worker is a single static binary — no dependencies, no configuration, one
per platform — which fetches its own Python, its own ffmpeg and its own audio
models on first run. The notebook fetches it through the same install script
the site publishes at <https://karaokie.app/install.sh>, so what runs here is
what runs on everybody else's machine.

Every other way to run one, and who is running one now:
<https://karaokie.app/worker>.

## Licence

MIT — see [LICENSE](LICENSE). Fork it, change it, run it against your own
server; the notebook is two cells and there is nothing precious in it.

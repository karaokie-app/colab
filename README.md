# karaokie worker, on a borrowed GPU

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/karaokie-app/colab/blob/main/karaokie_worker.ipynb)
[![Open in Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/karaokie-app/colab/main/kaggle_worker.ipynb)

[karaokie.app](https://karaokie.app) turns any song into a karaoke track:
the voice separated from the music, and every word of the lyrics placed
against it. That is a few minutes of work for a graphics card, and it is done
by whoever lends one — not by the small machine that serves the site.

This repository holds two notebooks, one for each place that will lend you a
graphics card for nothing. Either one borrows it, puts it on the queue, and
hands the finished songs back; nothing is installed on your own machine and
there is no account to make with karaokie.

- **[karaokie_worker.ipynb](karaokie_worker.ipynb)** for Colab. Choose **T4
  GPU** under Runtime ▸ Change runtime type, then run the two cells.
- **[kaggle_worker.ipynb](kaggle_worker.ipynb)** for Kaggle, which publishes
  its quota — about thirty GPU-hours a week — rather than leaving you to guess
  at it. Two switches on the right have to be turned on first: **Accelerator ▸
  GPU T4 x2**, and **Internet ▸ On**, which needs a phone-verified account.

The first cell of either checks what the place in question is inconsistent
about — whether the machine really did get a card, whether it can reach the
internet at all, and whether YouTube will answer it, since datacentre
addresses are the ones asked to prove they are not a robot. The second
downloads the worker, checks it against its published SHA-256, and runs it.

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

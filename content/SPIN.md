- https://github.com/nkolot/SPIN/

## Run on my Arch Linux 
This is run on CPU (because it's faster than GPU on my machine)
```bash
conda create -y -n spin python=3.10
conda activate spin
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
git clone https://github.com/nkolot/SPIN.git 
cd SPIN
git checkout origin/cuda11_fix
pip install -r requirements.txt
sh fetch_data.sh
```

Install `basicModel_neutral_lbs_10_207_0_v1.0.0.pkl` from [Smplify](https://smplify.is.tue.mpg.de/download.php)
Then run `mkdir -p data/smpl` and this
```py
# Get SMPL
def convert_pkl(old_pkl, new_pkl):
    """
    Convert a Python 2 pickle to Python 3
    """
    import dill
    import pickle

    # Convert Python 2 "ObjectType" to Python 3 object
    dill._dill._reverse_typemap["ObjectType"] = object

    # Open the pickle using latin1 encoding
    with open(old_pkl, "rb") as f:
        loaded = pickle.load(f, encoding="latin1")

    # Re-save as Python 3 pickle
    with open(new_pkl, "wb") as outfile:
        pickle.dump(loaded, outfile)

convert_pkl('basicModel_neutral_lbs_10_207_0_v1.0.0.pkl', 'data/smpl/SMPL_NEUTRAL.pkl')

```
In `demo.py`,
```py
device = torch.device('cpu')
...
checkpoint = torch.load(args.checkpoint, map_location=torch.device('cpu'))
```
```sh
python demo.py --checkpoint=data/model_checkpoint.pt --img=examples/im1010.jpg --openpose=examples/im1010_openpose.json
```

- Inference time on my CPU: 0.07s
- Inference time on my GPU: 0.15s

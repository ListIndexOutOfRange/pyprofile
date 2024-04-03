# A simple time and memory Python profiler

## Installation

`pip install tmprofile`


## Usage

### 1. As a context manager

```python
from tmprofile import Profile

with Profile(name, ...) as profiler:
    f(...) # some intensive code
# profile is automatically saved as a json file.
# display elapsed time, RAM & VRAM consumption evolution
profiler.print()
profiler.plot()
```

### 2. As a decorator

```python
from tmprofile import profile

@profile()
f(...) # some intensive code
# profile is automatically saved as a json file.
```

## Parameters

- `name (str)`: Name of the profiler. Will be used to name the saved file. Required for context manager. For decorator, will use fonction'name if no name is provided.
- `verbose (bool)`: If True, will print logged values at the end of profiling (i.e. on exit as a context manager, on function's return as a decorator). Defaults to False.
- `gpu_idx (int)`: Which gpu's VRAM consumption has to be monitored. Default to `0`.
- `time_delta (float)`: Time to wait (in second) between two RAM / VRAM consumption logging. Defaults to `0.2`.
- `output_dir (str | Path)`: Where to write the logged values (as json). Defaults to `.tmprofile`.
- `filename (str | Path, optional)`: Name of the saved json file. If no name is given, will used the profiler name (see `name` above).


## Disclaimer

The core of this code (asynchronous RAM/VRAM logging) is taken from Thomas Rouch's code [here](https://betterprogramming.pub/ram-and-vram-profiling-in-python-bf99876e985f).
    



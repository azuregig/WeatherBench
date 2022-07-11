# Run WeatherBench on Azure

|#|Mode | Pros | Cons | Commentary |
|--|-- |-- |--|--|
|1| interactively on a single Compute Instance|most similar to notebook-based interactive data science, ability to switch machine size|no distribution, not intended for working with fully customised environments||
|2| submit individual jobs to Compute Target (including clusters)|scaleable, full control over environments|non-interactive|
|3| define reusable components and pipelines |repeatable, componentised, automatable |non-interactive|

## 1. Interactive single-machine
Outline:
- provision a compute instance (one-off)
- adapt environment
- 

**Consideratons and Limitations**:
Compute *Instances* are different from other AML Compute *Targets* (e.g AML compute clusters) in that they are intended to be a *fully managed* development environment for the purpose of orchestrating and working with Azure ML assets. As such, they come with pre-configured python environments curated for this purpose, and don't provide tooling for managing custom environments. Here, we bypass the curated environment with standard conda operations to create a custom environment, and show how the compute instance can be used as a simple task-agnostic cloud VM. 

Steps
1. Create the compute instance:
```
az ml compute create -f interactive/computeinstance.yml
```

2. Connect to the compute instance:


3. create the environment:

```py
conda deactivate
# (do this twice if you still see active conda environments)
conda env create -f interactive/environment.yml
```

4. ensure the environment is visible to jupyter:
```
conda activate weatherbench
ipython kernel install --name weatherbench --display-name weatherbench
```


## 
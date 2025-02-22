# Function_usage

## Download 

Please download 'Template.zip'.

- **datasets**：store datasets
- **export**：store the model
- **mats**：store intermediate results or statistics
- **result**：store the pretrained parameters of the model
- **your script**：should be placed at the same level as 'export'


## Usage Guide for `heatmap_generator` Package

The `heatmap_generator` package provides tools to visualize the different stages results of our RPCANet++ on various scenarios from different datasets.

### Installation

First, install the package using `pip`:

```bash
pip install heatmap-generator
```

### Importing the Package

Import the package in your Python script:

```python
from heatmap_generator import HeatmapGenerator
```

### Available Functions

The package includes the following functions:

1. `heatmap_gen = HeatmapGenerator(model_name="rpcanetma9",model_path="./result/best.pkl", use_cuda=True)`
2. `heatmap = heatmap_gen.generate_heatmap(img_path="./datasets/test.png",data_name="test",output_mat="./heatmap/mat",output_png="./heatmap/png")`


### Function Descriptions and Examples

#### 1. `heatmap_gen = HeatmapGenerator(model_name="rpcanetma9",model_path="./result/best.pkl", use_cuda=True)`

The `heatmap_gen` function in the `heatmap_generator` package allows users to initialize the RPCANet model with pretrained parameters.

#### 2. `heatmap = heatmap_gen.generate_heatmap(img_path="./datasets/test.png",data_name="test",output_mat="./heatmap/mat",output_png="./heatmap/png")`

The `heatmap` function in the `heatmap_generator` package allows users to draw and save the heatmap from different stages.

#### Function Parameters

The `heatmap_gen` function accepts the following parameters:
- `model_name`: refer to the model which is underestimated.
- `model_path`: the pretrained parameters pkl path.
- `use_cuda`: Determined whether use GPU for acceleration.

The `heatmap` function accepts the following parameters:
- `img_path`: refer to the testing image.
- `data_name`: refer to the name of testing image.
- `output_mat`: save path for result with .m format.
- `output_png`: save path for result with .png format.

#### Examples

1. **For given model RPCANetma9**

   Draw the heatmat results of Background, Sparse, and Merge from 6 stages.

   ```python
    from heatmap_generator import HeatmapGenerator
    heatmap_gen = HeatmapGenerator(model_name="rpcanetma9",model_path="./result/best.pkl", use_cuda=True)

    heatmap = heatmap_gen.generate_heatmap(
        img_path="./datasets/NUDT-SIRST/test/xxxxx.png",
        data_name="NUDT-SIRST",
        output_mat="./mats/heatmap",
        output_png="./mats/heatmap/png"
    )
   ```

## Usage Guide for `lowrank_generator` Package

The `lowrank_generator` package provides tools to calculate and draw the low-rank property of results from different stages of RPCANet on various datasets.

### Installation

First, install the package using `pip`:

```bash
pip install lowrank-generator
```

### Importing the Package

Import the package in your Python script:

```python
from lowrank_generator import Lowrank_calculator
```

### Available Functions

The package includes the following functions:

1. `Lowrank_C = Lowrank_calculator(model_name="rpcanetma9",model_path="./results/best.pkl", use_cuda=True)`
2. `lowrank = Lowrank_C.calculate(img_path="./datasets/test",model_name="rpcanetma9",data_name="data_name",save_dir= './mats/lowrank')`
3. `draw_lowrank = Lowrank_C.draw_lowrank(model_name="rpcanetma9",data_name="data_name",mat_dir= './mats/lowrank',save_dir = './mats/lowrank/figure')`


### Function Descriptions and Examples

#### 1. `Lowrank_C = Lowrank_calculator(model_name="rpcanetma9",model_path="./results/best.pkl", use_cuda=True)`

The `Lowrank_C` function in the `lowrank_generator` package allows users to initialize the RPCANet model with pretrained parameters.

#### 2. `lowrank = Lowrank_C.calculate(img_path="./datasets/test",model_name="rpcanetma9",data_name="test",save_dir= './mats/lowrank')`

The `lowrank` function in the `lowrank_generator` package allows users to calculate Singular Value accross different stages and save with .m format.

#### 2. `draw_lowrank = Lowrank_C.draw_lowrank(model_name="rpcanetma9",data_name="test",mat_dir= './mats/lowrank',save_dir = './mats/lowrank/figure')`

The `draw_lowrank` function in the `lowrank_generator` package allows users to draw Low-rankness verification of differnet stages of models and save with .png format.

#### Function Parameters

The `Lowrank_C` function accepts the following parameters:
- `model_name`: refer to the model which is underestimated.
- `model_path`: the pretrained parameters pkl path.
- `use_cuda`: Determined whether use GPU for acceleration.

The `lowrank` function accepts the following parameters:
- `img_path`: refer to the testing image set.
- `model_name`: refer to the model which is underestimated.
- `data_name`: refer to the name of testing image.
- `save_dir`: save path for low rankness result with .m file.

The `draw_lowrank` function accepts the following parameters:
- `model_name`: refer to the model which is underestimated.
- `data_name`: refer to the name of testing image.
- `save_dir`: save path for low rankness result with .png file.


#### Examples

1. **For given model RPCANetma9**

   Calculate and draw the low-rankness verification of different stages of RPCANet.

   ```python
    from lowrank_generator import Lowrank_calculator
    # Load model
    Lowrank_C = Lowrank_calculator(model_name="rpcanetma9",model_path="./result/best.pkl", use_cuda=True)
    
    # Calculate the low-rankness verification and save with .m format
    lowrank = Lowrank_C.calculate(
        img_path="./datasets/NUDT-SIRST/test",
        model_name="rpcanetma9",
        data_name="NUDT-SIRST",
        save_dir= './mats/lowrank'
    )
    
    # Draw the low-rankness verification and save with .png format
    draw_lowrank = Lowrank_C.draw_lowrank(
        model_name="rpcanetma9",
        data_name="NUDT-SIRST",
        mat_dir= './mats/lowrank',
        save_dir = './mats/lowrank/figure'
    )
   ```





## Usage Guide for `sparsity_generator` Package

The `sparsity_generator` package provides tools to calculate the sparsity of results from different stages of RPCANet on various datasets.

### Installation

First, install the package using `pip`:

```bash
pip install sparsity-generator
```

### Importing the Package

Import the package in your Python script:

```python
from sparsity_generator import Sparsity_calculator
```

### Available Functions

The package includes the following functions:

1. `Sparsity_C = Sparsity_calculator(model_name="rpcanetma9",model_path="./result/best.pkl", use_cuda=True)`
2. `Sparsity = Sparsity_C.calculate(img_path="./datasets/test",model_name="rpcanetma9",data_name="test",save_dir = './mats/sparsity')`



### Function Descriptions and Examples

#### 1. `Sparsity_C = Sparsity_calculator(model_name="rpcanetma9",model_path="./result/best.pkl", use_cuda=True)`

The `Sparsity_C` function in the `sparsity_generator` package allows users to initialize the RPCANet model with pretrained parameters.

#### 2. `Sparsity = Sparsity_C.calculate(img_path="./datasets/test",model_name="rpcanetma9",data_name="test",save_dir = './mats/sparsity')`

The `Sparsity` function in the `sparsity_generator` package allows users to calculate Sparsity accross different stages and save with .m format.

#### Function Parameters

The `Sparsity_C` function accepts the following parameters:
- `model_name`: refer to the model which is underestimated.
- `model_path`: the pretrained parameters pkl path.
- `use_cuda`: Determined whether use GPU for acceleration.

The `Sparsity` function accepts the following parameters:
- `img_path`: refer to the testing image set.
- `model_name`: refer to the model which is underestimated.
- `data_name`: refer to the name of testing image.
- `save_dir`: save path for sparsity result with .m file.


#### Examples

1. **For given model RPCANetma9**

   Calculate the sparsity of results from different stages of RPCANet.

   ```python
    from sparsity_generator import Sparsity_calculator
    # load model
    Sparsity_C = Sparsity_calculator(model_name="rpcanetma9",model_path="./result/best.pkl", use_cuda=True)

    # calculate sparsity and save as .m format
    Sparsity = Sparsity_C.calculate(
        img_path="./datasets/NUDT-SIRST/test",
        model_name="rpcanetma9",
        data_name="NUDT-SIRST",
        save_dir = './mats/sparsity'
    )


   ```


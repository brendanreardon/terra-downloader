# Terra Downloader
A simple script to download columns from the Terra datamodel.

## Installation

### System requirements
To use terra storage helper, you must have the following set up on your system
- [Google Cloud SDK](https://cloud.google.com/sdk/)
- Python 3

Google Cloud and Terra use [Google Cloud SDK](https://cloud.google.com/sdk/) to manage authentication. The [application default credentials](https://cloud.google.com/sdk/gcloud/reference/auth/application-default/login) will be used. **Please walk through Google's wonderful install and set up documentation if you have not**. To login and set an application default, make sure that you've run the following,
```bash
gcloud auth login
gcloud auth application-default login
```

You may need to export your google cloud auth token, add this to your bash profile:
```bash
export GCS_OAUTH_TOKEN=`gcloud auth application-default print-access-token`
```

### Download this software from Github
This package can be download through Github on the website or by using terminal. To download on the website, navigate to the top of this page, click the green `Clone or download` button, and select `Download ZIP`. This will download this repository in a compressed format. To install using Github on terminal, type 

```bash
git clone https://github.com/brendanreardon/terra-downloader.git
cd terra-downloader
```

### Install Python dependencies
Terra Downloader uses Python 3.7. We recommend using a [virtual environment](https://docs.python.org/3/tutorial/venv.html) and running Python with either [Anaconda](https://www.anaconda.com/download/) or  [Miniconda](https://conda.io/miniconda.html). 

To create a virtual environment and install dependencies with Anaconda or Miniconda, run the following from this repository's directory:
```bash
conda create -y -n terra-downloader python=3.7
conda activate terra-downloader
pip install -r requirements.txt
```

If you are using base Python, you can create a virtual environment and install dependencies by running:
```bash
virtualenv terra-downloader
source activate terra-downloader/bin/activate
pip install -r requirements.txt
```

## Usage
The script downloader.py can be used to download all elements in a column in a data model. A folder named after the specified column name is created and files are deposited in there.

### Required arguments:
```
--namespace 	<string>	Workspace's namespace
--workspace	<string>	Workspace's name
--entity_type	<string>	Entity type, or table, in the datamodel
--column	<string>	Column name for download
```

### Example
In this example, we download the column `oncotated_maf` from the workspace `my-test-namespace/my-test-workspace` from the pair table.
```bash
python downloader.py --namespace my-test-namespace --workspace --my-test-workspace --entity_type pair --column oncotated_maf
```


# I/O Plugin

A plugin that contains standard import/export utilities.

## Installation

```shell
fiftyone plugins download \
    https://github.com/voxel51/fiftyone-plugins \
    --plugin-names @voxel51/io
```

Refer to the [main README](https://github.com/voxel51/fiftyone-plugins) for
more information about managing downloaded plugins and developing plugins
locally.

## Usage

1.  Launch the App:

```py
import fiftyone as fo
import fiftyone.zoo as foz

dataset = foz.load_zoo_dataset("quickstart")
session = fo.launch_app(dataset)
```

2.  Press `` ` `` or click the `Browse operations` action to open the Operators
    list

3.  Select any of the operators listed below!

## Operators

### add_samples

Use this operator to add samples to an existing dataset by specifying a
directory or glob pattern of media paths for which you want to create new
samples.

This operator is essentially a wrapper around the following import recipes:

```py
# Directories
dataset.add_images_dir(input_dir)
dataset.add_videos_dir(input_dir)

# Glob patterns
dataset.add_images_patt(glob_patt)
dataset.add_videos_patt(glob_patt)
```

### export_samples

You can use this operator to export your current dataset or view to disk in any
supported format.

This operator is essentially a wrapper around the following
[export recipe](https://docs.voxel51.com/user_guide/export_datasets.html#basic-recipe):

```py
# The directory to which to write the export
export_dir = "/path/for/export"

# The type of dataset to export
dataset_type = fo.types.COCODetectionDataset  # for example

# The name of the sample field containing the labels to export
label_field = "ground_truth"

# Whether to include the media files
export_media = True

dataset_or_view.export(
    export_dir=export_dir,
    dataset_type=dataset_type,
    label_field=label_field,
    export_media=export_media,
)
```

where the operator's form allows you to configure the export location, dataset
type, and necessary label field(s), if applicable.

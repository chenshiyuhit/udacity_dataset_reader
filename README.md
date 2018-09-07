# udacity_dataset_reader

Python scripts to read and dump data from the rosbag format used in the udacity self-driving dataset(s).

## Udacity datasets

[self-driving-car/datasets](https://github.com/udacity/self-driving-car/tree/master/datasets)

## Dependencies

    python-pandas
    python-dateutil
    ...

## Usage

Run the python scripts for dumping to images + csv or Tensorflow sharded records files.

### Dump to images + CSV

    python bagdump.py -i [local dir with folders containing bag files] -o [local output dir] -- [args to pass to python script]

For example, if your dataset bags are in /data/dataset.bag, and you'd like the output in /data/output:

    python bagdump.py -i /home/.../data -o /home/.../data/output

The same as above, but you want to convert to png instead of jpg:

    python bagdump.py -i /home.../.../data -o /home/.../data/output -- -f png

### Dump to Tensorflow sharded files

Same basic arguments as for bagdump above. There are some additional arguments of note to pass to the python script.

The default arguments write all cameras into the same sharded stream along with latest steering entry. To write images to three separate streams, one for each camera, add an -s (or --separate) argument.

i.e.

    python bag2tf.py -i /data -o /output -- --separate


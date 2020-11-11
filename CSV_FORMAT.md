# Universal Data Tool Format (\*.udt.csv) Specification

A `*.udt.csv` file is a [CSV](https://tools.ietf.org/html/rfc4180) representation of a Universal Data Tool interface, sample data and labels.

A `*.udt.csv` file can be used the same way as a `*.udt.json` file. An example `*.udt.csv` file is show below:

| path      | .                                                                                                                        | imageUrl                                                                              | annotation | annotation.regionType | annotation.centerX | annotation.centerY | annotation.width  | annotation.height | annotation.classification | annotation.labels | annotation.color  |
| --------- | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------- | ---------- | --------------------- | ------------------ | ------------------ | ----------------- | ----------------- | ------------------------- | ----------------- | ----------------- |
| interface | {"type":"image_segmentation","labels":["valid","invalid"],"regionTypesAllowed":["bounding-box"],"multipleRegions":false} |                                                                                       |            |                       |                    |                    |                   |                   |                           |                   |                   |
| samples.0 |                                                                                                                          | https://s3.amazonaws.com/asset.workaround.online/example-jobs/sticky-notes/image1.jpg |            | bounding-box          | 0.284214473190851  | 0.331271091113611  | 0.364454443194601 | 0.111361079865017 | valid                     |                   | hsl(185,100%,50%) |
| samples.1 |                                                                                                                          | https://s3.amazonaws.com/asset.workaround.online/example-jobs/sticky-notes/image2.jpg | null       |                       |                    |                    |                   |                   |                           |                   |                   |

A UDT CSV has one or more rows containing metadata, in the example above, we can see the `interface` row has some information regarding how to construct the interface to edit the samples.

The majority of the lines of a UDT CSV file are the samples. Each sample row starts with `samples.XXX` where `XXX` is the index of the sample. The properties and annotation of each dataset are then listed on the right.

For information on how this is converted to and from a JSON representation [see the JAC CSV format specification](https://github.com/seveibar/jac-format).

## Motivation

The Universal Data Tool format is natively in JSON, but many times it's easier to inspect and process data in a simple CSV format where each row represents a sample. However, limitations to how metadata can be stored in CSV files make this difficult. As a result we store some metadata in the first rows of a `*.udt.csv` file.

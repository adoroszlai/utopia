# Deployment utilities

## Analysis

### `gantt_chart`

Creates a [Gantt chart](https://en.wikipedia.org/wiki/Gantt_chart) (in [Mermaid](https://mermaidjs.github.io/) [format](https://mermaidjs.github.io/gantt.html)) of cluster deployment tasks based on Ambari agent command input/output files.

Requires [`jq` (command-line JSON processor)](https://stedolan.github.io/jq/).

#### Usage

 1. Store Ambari agent command data (`command*json`, `output*txt`) in a subdirectory for each host in the cluster.
 2. Pass the directories to `gantt_chart`, and save the output in some file.
    ```
    ./gantt_chart host1 host2 ... > gantt.mmd
    ```
 3. Render the output using Mermaid.
    ```
    docker run --rm -v $(pwd):/mmd adoroszlai/mmdc -i gantt.mmd -o gantt.png
    ```

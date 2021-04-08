### cluster_block_exception [FORBIDDEN/12/index read-only / allow delete (api)];

- *** Ref link **
- https://stackoverflow.com/questions/50609417/elasticsearch-error-cluster-block-exception-forbidden-12-index-read-only-all
- https://selleo.com/til/posts/esrgfyxjee-how-to-fix-elasticsearch-forbidden12index-read-only
- https://gist.github.com/hkulekci/686ab6a9d2583faf3ce6b8c528ea300f

check the diskspace in elasticsearch

Goto index_management and delete the old indexes then follow the any one of the solutions

- https://your-kibana/app/kibana#/management/elasticsearch/index_management/indices?_g=()
Note : change the kibana url according to your kibana

### Solution 1

Open dev_tools in kibna and run query
- https://your-kibana/app/kibana#/dev_tools/console?_g=()
Note : change the kibana url according to your kibana


```
PUT _all/_settings
{
  "index": {
    "blocks": {
      "read_only_allow_delete": "false"
    }
  }
}
```

### Solution 2

Run the below curl command

```
curl -XPUT -H "Content-Type: application/json" https://[YOUR_ELASTICSEARCH_ENDPOINT]:9200/_all/_settings -d '{"index.blocks.read_only_allow_delete": null}'

```
Note : change the elasticsearch url according to your elasticsearch

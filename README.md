# project-estrella
Project-Estrella goal is to operationalize the execution of parameterized `R` modules. 

# deploying the resources
```bash
azure group create -n <your-resource-group-name> -l "West Europe"
azure group deployment create -f "azuredeploy.json" -e "azuredeploy.parameters.json" -g <your-resource-group-name> -n <your-deployment-name>

```

# cloning the repo
in addition to just cloning the repo, you also need to fetch the submodules:

```
git clone
git submodule init 
git submodule update --init --remote
git submodule foreach git checkout master
git submodule foreach git pull origin
```

## integrate with Fortis
To integrate the Estrella predictions into Fortis, one simply adds a prediction message to the `locationinferenceinput` Azure queue.

Fortis input message format:
```js
{
    'source': 'ewars-messages',
    'created_at': moment().toISOString(),
    'message' : {
        'message' : "",
        'title' : "",
        'link' : "",
        'user_id' : ""
        'lang' :"",
        'id' : "",
        'originalSources' : ["EWARS"],
        'geo' : {
            lat/lon or lon/lat
        }
    }
}
```

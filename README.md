# project-estrella
Project-Estrella goal is to operationalize the execution of coefficient based calculations. 

# cloning the repo
To automatically deploy the solution and to benefit from continuous delivery, you need to fork the repo. To work with the repos, you also need to fetch the submodules:

```
git clone
git submodule init 
git submodule update --init --remote
git submodule foreach git checkout master
git submodule foreach git pull origin
```

# deploying the resources

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://azuredeploy.net/)

or deploy 
```bash
azure group create -n <your-resource-group-name> -l "West Europe"
azure group deployment create -f "azuredeploy.json" -e "azuredeploy.parameters.json" -g <your-resource-group-name> -n <your-deployment-name>
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

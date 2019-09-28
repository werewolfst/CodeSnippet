## 简易版的判断用户github上是否star了某个项目

```python
import requests

def check(repo_list, direct_repo):
    status = False
    for item in repo_list:
        if item["full_name"] == direct_repo:
            status = True
            break
    
    return status


def check_stared(username, direct_repo):
    url = "https://api.github.com/users/%s/starred" % username
    stared = False

    while True:
        res = requests.get(url)
        results = res.json()
        status = check(results, direct_repo)
        if status:
            stared = True
            break

        if "next" in res.links:
            url = res.links["next"]["url"]
        else:
            break
    
    return stared
    
if __name__ == "__main__":
    username = "werewolfst"
    direct_repo = "NuoHui/fe-note"
    result = check_stared(username, direct_repo)

    print("*******************")
    print("Result: %s" % result)
    print("*******************")
```
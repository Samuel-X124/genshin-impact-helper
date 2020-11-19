<div align="center">
<h1 align="center">
Genshin Impact Helper
</h1>

![Genshin Impact Helper](https://i.loli.net/2020/11/18/3zogEraBFtOm5nI.jpg)
[![GitHub stars](https://img.shields.io/github/stars/y1ndan/genshin-impact-helper?style=flat-square)](https://github.com/y1ndan/genshin-impact -helper/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/y1ndan/genshin-impact-helper?style=flat-square)](https://github.com/y1ndan/genshin-impact -helper/network)
[![GitHub issues](https://img.shields.io/github/issues/y1ndan/genshin-impact-helper?style=flat-square)](https://github.com/y1ndan/genshin-impact -helper/issues)
[![GitHub contributors](https://img.shields.io/github/contributors/y1ndan/genshin-impact-helper?style=flat-square)](https://github.com/y1ndan/genshin-impact -helper/graphs/contributors)
![Github workflow status](https://img.shields.io/github/workflow/status/y1ndan/genshin-impact-helper/Genshin%20Impact%20Helper?label=status&style=flat-square)

</div>

## 📎Foreword

Yuanshen is the only game I have seen where the main body of the game is separated from the check-in benefits. In order to check-in, players have to download the Miyoushe App.

In all fairness, the current daily sign-in rewards are really not good, as everyone knows it is mosquito legs. In fact, you can choose to ignore the sign-in, and there is no big loss if you do not sign it; or you can choose to sign-in manually, but if you forget to check in, it will be a headache.

I admit that I am greedy for the rewards of the **6W+** Mora and Purple Experience Book, so I slapped this item to realize automatic daily check-in.

**If you think this project is helpful to you, please order `Star` QAQ❤**

## 📐Deploy

### 1. Fork warehouse

* Project address: [github/genshin-impact-helper](https://github.com/y1ndan/genshin-impact-helper)
* Click `Fork` in the upper right corner to go to your account

> ![fork](https://i.loli.net/2020/10/28/qpXowZmIWeEUyrJ.png)

### 2. Get Cookies

Open the browser https://bbs.mihoyo.com/ys/ and log in to the account

#### 2.1 Method One

* Press `F12`, open `Developer Tools`, find `Network` and click
* Press `F5` to refresh the page, and copy `Cookie` as shown below

> ![cookie](https://i.loli.net/2020/10/28/TMKC6lsnk4w5A8i.png)

#### 2.2 Method Two

* Copy the following code
```
JSON.stringify({
  Cookie: document.cookie
});
```
* Press `F12`, open `Developer Tools`, find `Console` and click
* Paste the code on the command line and run it to get output information similar to `"{"Cookie":"xxxxxx"}"`
* The `xxxxxx` part is the `Cookie` to be copied

### 3. Add Cookie to Secrets

* Back to the project page, click on `Settings`-->`Secrets`-->`New secret`

> ![new-secret.png](https://i.loli.net/2020/10/28/sxTuBFtRvzSgUaA.png)

* Create a secret named `COOKIE`, the value is the content of `Cookie` copied in `Step 2`, and finally click `Add secret`

> ![add-secret](https://i.loli.net/2020/10/28/sETkVdmrNcCUpgq.png)

### 4. Enable Actions

> Actions is disabled by default. After the Fork, you need to execute it manually, and it will only be activated if it runs successfully.

Return to the main page of the project, click on the top `Actions`, then click on the left side `Genshin Impact Helper`, then click on `Run workflow`
    
> ![run](https://i.loli.net/2020/10/28/5ylvgdYf9BDMqAH.png)

At this point, the deployment is complete.

## 🔍Result

When you have completed the above process, you can click on `Genshin Impact Helper`-->`build`-->`Run sign` on the `Actions` page to view the results.

### Sign in successfully

If successful, a message similar to `"result": "Success"` will be output:

```
2020-11-18T22:11:45 INFO Sleep for 100 seconds ...
2020-11-18T22:13:26 INFO UID is 102***054
2020-11-18T22:13:27 INFO {
  "result": "Success",
  "message": "{\"retcode\": 0, \"message\": \"OK\", \"data\": {\"code\": \"ok\"}}"
}
```

### Sign in failed

If it fails, a message similar to `"result": "Failed"` will be output:

```
2020-11-17T22:11:33 INFO Sleep for 54 seconds ...
2020-11-17T22:12:28 INFO UID is 102***054
2020-11-17T22:12:29 INFO {
  "result": "Failed",
  "message": "{\"data\": null, \"message\": \"Request exception\", \"retcode\": -401}"
}
Error: Process completed with exit code 255.
```

At the same time, you will receive an email from GitHub with the title `Run failed: Genshin Impact Helper-master`.

## Update

Because there may be some changes on the request, the upstream source code needs to be changed to adapt to these changes. If you do not update the project source code, it will cause the check-in to fail. The update steps are as follows.

```
git clone https://github.com/<Your GitHub ID>/genshin-impact-helper.git
cd ./genshin-impact-helper
git pull https://github.com/y1ndan/genshin-impact-helper.git master
git push origin master
```

The above steps can be performed in any [Linux](https://zh.wikipedia.org/wiki/Linux), or installed in [Windows](https://zh.wikipedia.org/wiki/Microsoft_Windows) [ Git](https://zh.wikipedia.org/wiki/Git), then completed in the `Git Bash` software.

> 1. Git can be downloaded from [here](https://git-scm.com/downloads), and more information can be found [here](https://git-scm.com/book/).
> 2. After the update is completed, there is no need to redeploy Actions.

## Description

This code uses cookies to log in to the Miyoushe webpage through a simulated browser, and click on the page to complete the signature to realize the function. The sign-in function is implemented through the official public API, not a game plug-in.

## ❗️Attention

1. The program will automatically execute the sign-in process every morning, or it can be triggered manually through the above `step 4` at any time, please refer to [here](.github/workflows/main.yml)
2. When login fails, try to replace `Cookie` again
3. Support multiple accounts, use `#` to separate different `Cookie`
4. Support official service and B service

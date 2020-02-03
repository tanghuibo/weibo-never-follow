# 微博取关浏览器自动化脚本

## quick start

### 1. 进入关注页面

### 2. 打开控制台，运行如下脚本
```javascript
/**
 * 获取不再关注按钮
 */
function getNeverFollowBtn() {
    return document.querySelector("#Pl_Official_RelationMyfollow__95 > div > div > div > div.member_box > ul > li:nth-child(1) > div.member_wrap.clearfix > div.mod_info > div.opt > div:nth-child(3) > ul > li:nth-child(3) > a");
}

/**
 * 获取确认按钮
 */
function getConfirmBtn() {
    return document.querySelector("div.content > div.W_layer_btn.S_bg1 > a.W_btn_a.btn_34px");
}

function sleep(time) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(time);
        }, time);
    })
}

(async () => {
	//获取取关按钮
    let neverFollowBtn = getNeverFollowBtn();
    while (neverFollowBtn !== null) {
    	//点击取关按钮
        neverFollowBtn.click();
        await sleep(50);
        //点击确认框
        getConfirmBtn().click();
        await sleep(1000);
        //获取下一个取关按钮
        neverFollowBtn = getNeverFollowBtn();
    }
})();
```

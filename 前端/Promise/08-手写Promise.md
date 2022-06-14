```javascript
// Promise 构造函数
function Promise(excutor) {

    this.status = "pending";
    this.data = undefined;
    this.callbacks = [];
    const self = this;

    function resolve(value) {
        // 判断只能修改一次状态
        if (self.status !== "pending") {
            return;
        }

        // 将状态改为resolved
        self.status = "resolved";

        // 保存value数据
        self.data = value;

        // 调用成功的回调
        self.callbacks.forEach(item => {
            item.onResolved(value);
        });
    }

    function reject(reason) {
        if (self.status !== "pending") {
            return;
        }

        self.status = "rejected";
        self.data = reason;

        // 调用失败的回调
        self.callbacks.forEach(item => {
            item.onRejected(reason);
        });
    }

    try {
        excutor(resolve, reject);
    } catch (e) {
        reject(e);
    }
}


// then()
Promise.prototype.then = function (onResolved, onRejected) {
    const self = this;

    // 判断回调函数参数，实现异常穿透
    if (typeof onRejected !== "function") {
        onRejected = (reason) => {
            throw reason;
        }
    }

    return new Promise((resolve, reject) => {

        if (this.status === "pending") {
            // 保存回调函数
            this.callbacks.push({
                onResolved: function () {
                    try {
                        //执行成功回调函数
                        let result = onResolved(self.status);
                        //判断
                        if (result instanceof Promise) {
                            result.then(v => {
                                resolve(v);
                            }, r => {
                                reject(r);
                            })
                        } else {
                            resolve(result);
                        }
                    } catch (e) {
                        reject(e);
                    }
                },
                onRejected: function () {
                    try {
                        //执行成功回调函数
                        let result = onRejected(self.status);
                        //判断
                        if (result instanceof Promise) {
                            result.then(v => {
                                resolve(v);
                            }, r => {
                                reject(r);
                            })
                        } else {
                            resolve(result);
                        }
                    } catch (e) {
                        reject(e);
                    }
                }
            });
        }

        if (this.status === "resolved") {
            try {
                let result = onResolved(this.data);

                if (result instanceof Promise) {
                    result.then(
                        value => {
                            resolve(value);
                        },
                        reason => {
                            reject(reason);
                        }
                    )
                } else {
                    resolve(result);
                }
            } catch (error) {
                reject(error)
            }

        }

        if (this.status === "rejected") {

            try {
                let result = onRejected(this.data);
                if (result instanceof Promise) {
                    result.then(
                        value => {
                            resolve(value)
                        },
                        reason => {
                            reject(reason)
                        }
                    )
                } else {
                    resolve(result);
                }
            } catch (error) {

            }
        }

    })
}


// catch()
Promise.prototype.catch = function (onRejected) {
    return this.then(undefined, onRejected);

}


Promise.resolve = function (value) {
    return new Promise((resolve, reject) => {
        if (value instanceof Promise) {
            value.then(
                value => {
                    resolve(value);
                },
                reason => {
                    reject(reason);
                }
            )
        } else {
            resolve(value);
        }
    })
}


Promise.reject = function (reason) {
    return new Promise((resolve, reject) => {
        reject(reason);
    })
}


Promise.all = function (promises) {
    // 返回结果为Promise对象
    return new Promise((resolve, reject) => {
        let count = 0;

        // 存放成功结果
        let arr = [];

        // 遍历
        for (let i = 0; i < promises.length; i++) {
            promises[i].then(
                value => {
                    // 每个promise都成功才为成功
                    count++;

                    // 添加成功的结果
                    arr[i] = value;

                    // 判断所有promise对象都成功了
                    if (count === promises.length) {
                        resolve(arr);
                    }
                },
                reason => {
                    reject(reason);
                }
            )
        }
    })
}


Promise.race = function (promises) {
    return new Promise((resolve, reject) => {
        for (let i = 0; i < promises.length; i++) {
            promises[i].then(
                value => {
                    resolve(value);
                },
                reason => {
                    reject(reason);
                }
            )
        }
    })
}
```
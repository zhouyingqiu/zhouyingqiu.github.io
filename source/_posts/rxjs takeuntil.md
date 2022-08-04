

title: rxjs-takeUntil
date: 2022-08-03 20:30:29
update: 2022-08-03 20:30:29
categories: 技术
description: rxjs操作符之takeUntil
tags: ['rxjs', 'angular']
---

** takeUntil<T>(notifier: ObservableInput<any>): MonoTypeOperatorFunction<T> **
> 让值传递，直到第二个 Observable(notifier)发出一个值。源Observer将取消订阅。

#### 官网图解
![takeUntil图解](/img/take-until.jpg)

#### 使用场景举例
##### 例子1
> 当click事件触发后，源observer订阅被取消，控制台停止打印

```typescript
import { interval, fromEvent, takeUntil } from 'rxjs';

const source = interval(1000);
const clicks = fromEvent(document, 'click');
const result = source.pipe(takeUntil(clicks));
result.subscribe(x => console.log(x));

```

##### 例子2
> 创建一个供需要自动取消oversver订阅的组件的基类

```typescript
export interface ThyUnsubscribe extends OnDestroy {
    ngUnsubscribe$: Subject<any>;
}

// 封装一个基类，在组件销毁时触发一个observer
export function mixinUnsubscribe<T extends Constructor<{}>>(base: T): Constructor<ThyUnsubscribe> & T {
    return class Mixin extends base {
        ngUnsubscribe$ = new Subject();

        constructor(...args: any[]) {
            super(...args);
        }

        ngOnDestroy() {
            this.ngUnsubscribe$.next();
            this.ngUnsubscribe$.complete();
        }
    };
}

// 组件类需要自动取消订阅的流
@Component({...})
export class SomeComponent extends mixinUnsubscribe(MixinBase) implements OnInit {
  ngOnInit() {
    this.some$
      .pipe(takeUntil(this.ngUnsubscribe$))
      .subscribe(() => {})
  }
}
```



---
title: Code-Optimization (2)
author: せいい
top: true
cover: false
toc: true
tags:
  - ES6
  - 工作经验
categories:
  - Frontend
date: 2021-01-07 22:42:10
summary: 代码优化 -- 函数篇
---

## 背景
* 对代码的优化过程中，有了一点小心得。

## 理想的函数
1. 清晰的定义
2. 两三个参数
3. 只做一件事

* 优化前
```javascript
//函数定义
export const setUrl = (
    pathname: string,
    urlSort: string,
    urlKeywords: string,
    page: number,
    pageSize: number,
    keywords?: string,
    sort?: string,
) => {
    let url: string;
    if (sort && setSortParam(sort) === urlSort) {
        // handleChange向けのコード
        urlKeywords === '{}'
            ? (url =
                  pathname +
                  '?page=' +
                  page +
                  '&pagesize=' +
                  pageSize +
                  '&sort=' +
                  setSortParam(sort))
            : (url =
                  pathname +
                  '?page=' +
                  page +
                  '&pagesize=' +
                  pageSize +
                  '&filter=' +
                  urlKeywords +
                  '&sort=' +
                  setSortParam(sort));
    } else if (sort && setSortParam(sort) !== urlSort) {
        //他のページからソート場合、自動的に１ページへ戻る
        urlKeywords === '{}'
            ? (url = pathname + '?page=1&pagesize=' + pageSize + '&sort=' + setSortParam(sort))
            : (url =
                  pathname +
                  '?page=1&pagesize=' +
                  pageSize +
                  '&filter=' +
                  urlKeywords +
                  '&sort=' +
                  setSortParam(sort));
    } else if (!sort && keywords) {
        // handleSearch向けのコード
        // 他のページから検索場合、自動的に１ページへ戻りたいのため、pageは１に設定
        url =
            pathname +
            '?page=' +
            page +
            '&pagesize=' +
            pageSize +
            '&filter=' +
            keywords +
            '&sort=' +
            urlSort;
    } else {
        url = pathname + '?page=' + page + '&pagesize=' + pageSize +
        '&sort=' + urlSort;
    }
    return url;
};

//函数调用
//handleChange
history.push(
    setUrl(
        location.pathname,
        urlSort,
        filter,
        page,
        pageSize,
        '{}',
        sortParam,
    ),
);
//handleSearch
history.push(
    setUrl(
        location.pathname,
        urlSort,
        urlKeywords,
        1,
        pageSize,
        JSON.stringify(keywordsObj),
    ),
);
```

* 优化后
```typescript
//函数定义
type HandleChangeOptions = {
    pathname: string;
    page: number;
    pageSize: number;
    urlFilters: string;
    oldSort: string;
    newSort: string;
};
type HandleSearchOptions = {
    pathname: string;
    pageSize: number;
    filters: string;
    sort: string;
};
export const setHandleChangeUrl = (args: HandleChangeOptions) => {
    let url: string;
    if (args.newSort && setSortParam(args.newSort) === args.oldSort) {
        args.urlFilters === '{}'
            ? (url =
                  args.pathname +
                  '?page=' +
                  args.page +
                  '&pagesize=' +
                  args.pageSize +
                  '&sort=' +
                  args.oldSort)
            : (url =
                  args.pathname +
                  '?page=' +
                  args.page +
                  '&pagesize=' +
                  args.pageSize +
                  '&filter=' +
                  args.urlFilters +
                  '&sort=' +
                  args.oldSort);
    } else {
        args.urlFilters === '{}'
            ? (url =
                  args.pathname +
                  '?page=1&pagesize=' +
                  args.pageSize +
                  '&sort=' +
                  setSortParam(args.newSort))
            : (url =
                  args.pathname +
                  '?page=1&pagesize=' +
                  args.pageSize +
                  '&filter=' +
                  args.urlFilters +
                  '&sort=' +
                  setSortParam(args.newSort));
    }
    return url;
};
export const setHandleSearchUrl = (args: HandleSearchOptions) => {
    let url: string;
    const filterObj = JSON.parse(args.filters);
    Object.keys(filterObj).map((item) => {
        if (!filterObj[item]) {
            delete filterObj[item];
        }
        return true;
    });
    if (filterObj['status'] && filterObj['status'][0] === 'all') {
        delete filterObj['status'];
    }
    if (filterObj['roleId'] && filterObj['roleId'] === 'all') {
        delete filterObj['roleId'];
    }
    const filterStr = JSON.stringify(filterObj);
    filterStr === '{}'
        ? (url = args.pathname + '?page=1&pagesize=' + args.pageSize + '&sort=' + args.sort)
        : (url =
              args.pathname +
              '?page=1&pagesize=' +
              args.pageSize +
              '&filter=' +
              filterStr +
              '&sort=' +
              args.sort);
    return url;
};
//函数调用
//handleChange
history.push(
    setHandleChangeUrl({
        pathname: location.pathname,
        page: page,
        pageSize: pageSize,
        urlFilters: filter,
        oldSort: urlSort,
        newSort: sort,
    }),
);
//handleSearch
history.push(
    setHandleSearchUrl({
        pathname: location.pathname,
        pageSize: urlPageSize,
        filters: JSON.stringify(filtersObj),
        sort: urlSort,
    }),
);
```

## 小结
* 一开始的代码不够优雅很正常，先把功能实现了再通过层层迭代，逐渐优化
* 限于当时的认知写出了低质量的代码，视野开阔之后及时对代码进行重构
* 优化预定，虽然目前还不知方向在哪，有种在一亩三分地上疯狂耕耘的感觉

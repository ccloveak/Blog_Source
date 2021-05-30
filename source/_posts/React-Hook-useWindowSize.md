---
title: React Hook 'useWindowSize'
author: せいい
top: false
cover: false
toc: true
tags:
  - Hook
  - React
categories:
  - Frontend
date: 2021-05-30 17:40:46
summary: 监控页面大小的hook
---

## 需求

- 根据页面 size 展示不同的组件

## 实现

```typescript
const getSize = () => {
  return window.innerWidth > 1000 ? "large" : "small";
};
const useWindowSize = () => {
  const [size, setSize] = useState(getSize());
  useEffect(() => {
    const handler = () => {
      setSize(getSize());
    };
    window.addEventListener("resize", handler);
    return () => {
      window.removeEventListener("resize", handler);
    };
  }, []);
  return size;
};
```

## 使用

```typescript
const Demo = () => {
  const size = useWindowSize();
  return size === "small" ? <SmallComponent /> : <LargeComponent />;
};
```

## 关联知识点

- 事件监听，移除事件监听
- useEffect 里的 return

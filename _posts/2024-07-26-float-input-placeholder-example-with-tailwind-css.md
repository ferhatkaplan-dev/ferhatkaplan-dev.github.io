---
title: Float Input Placeholder Example With Tailwind CSS
date: 2024-07-26 03:30:00 +0300
categories: [programing, tailwind css]
tags: [tailwind css, react, typescript, placeholder animation, float placeholder]
description: "Learn how to enhance your forms with float placeholders using Tailwind CSS. This guide provides a clear example of implementing float placeholders in both HTML and React, showcasing practical code snippets and styling techniques for a sleek, user-friendly interface."
image:
  path: assets/img/post_images/2024-07-26-float-input-placeholder-example-with-tailwind-css-preview.webp
  lqip: assets/img/post_images/2024-07-26-float-input-placeholder-example-with-tailwind-css-preview-low.avif
  alt: float input placeholder preview image
lang: en
---

If you want to add a little more visuality to our input, we can use float placeholder. Here is an example written with Tailwind CSS.


![float placeholder input image](assets/img/post_images/1_OyfVK0yH-3Gz1Cq9BvFFYw.gif)
_float input placeholder example with tailwind css gif_

```html
<div class="relative">
  <input
    id="password"
    type="password"
    placeholder=""
    class="peer bg-black bg-opacity-50 px-4 pt-6 pb-2 w-full rounded border border-slate-600 text-white focus:ring-2 focus:ring-white outline-none invalid:border-red-500"
  />
  <label
    for="password"
    class="absolute text-slate-400 left-3 scale-75 top-2 peer-placeholder-shown:scale-100 peer-placeholder-shown:top-4 peer-focus:scale-75 peer-focus:top-2 duration-300"
  >
    Password
  </label>
</div>
```

If you want to use it in React, there is an example usage below.

```jsx
import { ComponentPropsWithoutRef } from "react";

type InputProps = ComponentPropsWithoutRef<"input"> & {
  label: string;
};

function Input({ label, type }: InputProps) {
  return (
    <div className="relative">
      <input
        id={label}
        type={type}
        placeholder=""
        className="peer bg-black bg-opacity-50 px-4 pt-6 pb-2 w-full rounded border border-slate-600 text-white focus:ring-2 focus:ring-white outline-none invalid:border-red-500"
      />
      <label
        htmlFor={label}
        className="absolute text-slate-400 left-3 scale-75 top-2 peer-placeholder-shown:scale-100 peer-placeholder-shown:top-4 peer-focus:scale-75 peer-focus:top-2 duration-300"
      >
        {label}
      </label>
    </div>
  );
}

export default Input;
```

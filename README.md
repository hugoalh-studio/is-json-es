# Is JSON (ES)

[**⚖️** MIT](./LICENSE.md)

[![GitHub: hugoalh-studio/is-json-es](https://img.shields.io/github/v/release/hugoalh-studio/is-json-es?label=hugoalh-studio/is-json-es&labelColor=181717&logo=github&logoColor=ffffff&sort=semver&style=flat "GitHub: hugoalh-studio/is-json-es")](https://github.com/hugoalh-studio/is-json-es)
[![JSR: @hugoalh/is-json](https://img.shields.io/jsr/v/@hugoalh/is-json?label=JSR%20@hugoalh/is-json&labelColor=F7DF1E&logoColor=000000&style=flat "JSR: @hugoalh/is-json")](https://jsr.io/@hugoalh/is-json)
[![NPM: @hugoalh/is-json](https://img.shields.io/npm/v/@hugoalh/is-json?label=@hugoalh/is-json&labelColor=CB3837&logo=npm&logoColor=ffffff&style=flat "NPM: @hugoalh/is-json")](https://www.npmjs.com/package/@hugoalh/is-json)

An ES (JavaScript & TypeScript) module to determine whether the item is a JSON.

## 🎯 Target

- Bun >= v1.1.0
- Cloudflare Workers
- Deno >= v1.42.0
  > **🛡️ Require Permission**
  >
  > *N/A*
- NodeJS >= v16.13.0

## 🔰 Usage

### Via JSR With `node_modules`

> **🎯 Supported Target**
>
> - Bun
> - Cloudflare Workers
> - NodeJS

1. Install via:
    - Bun
      ```sh
      bunx jsr add @hugoalh/is-json[@${Tag}]
      ```
    - NPM
      ```sh
      npx jsr add @hugoalh/is-json[@${Tag}]
      ```
    - PNPM
      ```sh
      pnpm dlx jsr add @hugoalh/is-json[@${Tag}]
      ```
    - Yarn
      ```sh
      yarn dlx jsr add @hugoalh/is-json[@${Tag}]
      ```
2. Import at the script:
    ```ts
    import ... from "@hugoalh/is-json";
    ```

> **ℹ️ Note**
>
> - Although it is recommended to import the entire module, it is also able to import part of the module with sub path if available, please visit [file `jsr.jsonc`](./jsr.jsonc) property `exports` for available sub paths.
> - It is recommended to import the module with tag for immutability.

### Via JSR With Specifier

> **🎯 Supported Target**
>
> - Deno

1. Import at the script:
    ```ts
    import ... from "jsr:@hugoalh/is-json[@${Tag}]";
    ```

> **ℹ️ Note**
>
> - Although it is recommended to import the entire module, it is also able to import part of the module with sub path if available, please visit [file `jsr.jsonc`](./jsr.jsonc) property `exports` for available sub paths.
> - It is recommended to import the module with tag for immutability.

### Via NPM With `node_modules`

> **🎯 Supported Target**
>
> - Cloudflare Workers
> - NodeJS

1. Install via:
    - NPM
      ```sh
      npm install @hugoalh/is-json[@${Tag}]
      ```
    - PNPM
      ```sh
      pnpm add @hugoalh/is-json[@${Tag}]
      ```
    - Yarn
      ```sh
      yarn add @hugoalh/is-json[@${Tag}]
      ```
2. Import at the script:
    ```ts
    import ... from "@hugoalh/is-json";
    ```

> **ℹ️ Note**
>
> - Although it is recommended to import the entire module, it is also able to import part of the module with sub path if available, please visit [file `jsr.jsonc`](./jsr.jsonc) property `exports` for available sub paths.
> - It is recommended to import the module with tag for immutability.

### Via NPM With Specifier

> **🎯 Supported Target**
>
> - Bun
> - Deno

1. Import at the script:
    ```ts
    import ... from "npm:@hugoalh/is-json[@${Tag}]";
    ```

> **ℹ️ Note**
>
> - Although it is recommended to import the entire module, it is also able to import part of the module with sub path if available, please visit [file `jsr.jsonc`](./jsr.jsonc) property `exports` for available sub paths.
> - It is recommended to import the module with tag for immutability.

### Via Remote Import

> **🎯 Supported Target**
>
> - Deno

1. Import at the script:
    ```ts
    /* Via GitHub Raw (Require Tag) */
    import ... from "https://raw.githubusercontent.com/hugoalh-studio/is-json-es/${Tag}/mod.ts";
    ```

> **ℹ️ Note**
>
> - Although it is recommended to import the entire module with the main path `mod.ts`, it is also able to import part of the module with sub path if available, but do not import if:
>
>   - it's file path has an underscore prefix (e.g.: `_foo.ts`, `_util/bar.ts`), or
>   - it is a benchmark or test file (e.g.: `foo.bench.ts`, `foo.test.ts`), or
>   - it's symbol has an underscore prefix (e.g.: `export function _baz() {}`).
>
>   These elements are not considered part of the public API, thus no stability is guaranteed for them.
> - Although there have 3rd party services which provide enhanced, equal, or similar methods/ways to remote import the module, beware these services maybe inject unrelated elements and thus affect the security.

## 🧩 API

- ```ts
  function isJSON(item: unknown): item is JSONValue;
  ```
- ```ts
  function isJSONArray(item: unknown): item is JSONArray;
  ```
- ```ts
  function isJSONObject(item: unknown): item is JSONObject;
  ```
- ```ts
  function isJSONPrimitive(item: unknown): item is JSONPrimitive;
  ```
- ```ts
  type JSONArray = JSONValue[];
  ```
- ```ts
  type JSONArrayExtend = JSONValueExtend[] | readonly JSONValueExtend[];
  ```
- ```ts
  type JSONObject = { [key: string]: JSONValue; };
  ```
- ```ts
  type JSONObjectExtend = { [key: string]: JSONValueExtend; };
  ```
- ```ts
  type JSONPrimitive = boolean | number | string | null;
  ```
- ```ts
  type JSONValue = JSONArray | JSONObject | JSONPrimitive;
  ```
- ```ts
  type JSONValueExtend = JSONArrayExtend | JSONObjectExtend | JSONPrimitive | undefined;
  ```

> **ℹ️ Note**
>
> For the prettier documentation, can visit via:
>
> - [Deno CLI `deno doc`](https://deno.land/manual/tools/documentation_generator)
> - [JSR](https://jsr.io/@hugoalh/is-json)

## ✍️ Example

- ```ts
  isJSON({
    a: 1,
    b: 2,
    c: 3,
    d: () => { }
  });
  //=> false
  ```
- ```ts
  isJSON({
    a: 1,
    b: 2,
    c: 3,
    d: new Map()
  });
  //=> false
  ```
- ```ts
  isJSON(NaN);
  //=> false
  ```
- ```ts
  isJSON(void 0);
  //=> false
  ```
- ```ts
  isJSON({
    a: 1,
    b: 2,
    c: 3
  });
  //=> true
  ```
- ```ts
  isJSON([1, 2, 3]);
  //=> true
  ```

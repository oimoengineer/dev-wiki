# これだけは理解して
## Inline Styles
直接コンポーネント内に記述できる

JSの記法で書く必要がある

タグごとにstyle={}で記載する

```
export const InlineStyle = () => {
  const containerStyle = {
    border: "solid 2px #392eff",
    borderRadius: "20px",
    padding: "8px",
    margin: "8px",
    display: "flex",
    justifyContent: "space-around",
    alignItems: "center",
  };
  const titleStyle = {
    margin: 0,
    color: "#3d84a8",
  };
  const buttonStyle = {
    backgroundColor: "#abedd8",
    border: "none",
    padding: "8px",
    borderRadius: "8px",
  };

  return (
    <div style={containerStyle}>
      <p style={titleStyle}>- Inline Styles -</p>
      <button style={buttonStyle}>FIGHT</button>
    </div>
  );
};

```

## CSS Modules
コンポーネントにimportする形で読み込む

CSSの記法をそのまま使用できる

クラス名が競合しないのが利点

CssModules.jsx
```
import classes from "./CssModules.module.scss";

export const CssModules = () => {
  return (
    <div className={classes.container}>
      <p className={classes.title}>- CSS Modules -</p>
      <button className={classes.button}>FIGHT!!</button>
    </div>
  );
};

```

CssModules.module.scss
```
.container {
  border: solid 2px #392eff;
  border-radius: 20px;
  padding: 8px;
  margin: 8px;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.title {
  margin: 0;
  color: #3d84a8;
}

.button {
  background-color: #abedd8;
  border: none;
  padding: 8px;
  border-radius: 8px;
  &:hover {
    background-color: #46cdcf;
    color: #fff;
    cursor: pointer;
  }
}

```

## Styled JSX
styleタグの中に直接cssを書くことが出来る。
classを指定するときもクラス名をそのまま指定できる。

```
export const StyledJsx = () => {
  return (
    <>
      <div className="container">
        <p>- styled JSX -</p>
        <button>FIGHT!!</button>
      </div>
      <style jsx="true">{`
        .container {
          border: solid 2px #392eff;
          border-radius: 20px;
          padding: 8px;
          margin: 8px;
          display: flex;
          justify-content: space-around;
          align-items: center;
        }
      `}</style>
    </>
  );
};

```

## styled components
直接スタイルをあてたコンポーネントを作成する。

シンプルでわかりやすいが、そのコンポーネントがスタイルをあてただけのコンポーネントなのか通常のコンポーネントなのか見分けがつきづらい。

⇒何かしらローカルルール的な命名規則で回避するといいかも。(先頭に必ず”S”を付けるとか)

Sassの記法が使用できる。

```
import styled from "styled-components";

export const StyledComponents = () => {
  return (
    <SContainer>
      <STitle>- Styled Components -</STitle>
      <SButton>FIGHT!!</SButton>
    </SContainer>
  );
};

// styleをあてたコンポーネントを作成する
const SContainer = styled.div`
  border: solid 2px #392eff;
  border-radius: 20px;
  padding: 8px;
  margin: 8px;
  display: flex;
  justify-content: space-around;
  align-items: center;
`;

const STitle = styled.p`
  margin: 0;
  color: #3d84a8;
`;

const SButton = styled.button`
  background-color: #abedd8;
  border: none;
  padding: 8px;
  border-radius: 8px;
  &:hover {
    background-color: #46cdcf;
    color: #fff;
    cursor: pointer;
  }
`;

```

## [Emotion](https://emotion.sh/docs/introduction)
様々なスタイルの当て方ができる。
どの記法を採用するのかはチーム内ですり合わせる必要がある。

```
/** @jsxRuntime classic */
/** @jsx jsx */
import { jsx, css } from "@emotion/react";
import styled from "@emotion/styled";

export const Emotion = () => {
  const containerStyle = css`
    border: solid 2px #392eff;
    border-radius: 20px;
    padding: 8px;
    margin: 8px;
    display: flex;
    justify-content: space-around;
    align-items: center;
  `;
  const titleStyle = css({
    margin: 0,
    color: "#3d84a8",
  });
  return (
    <div css={containerStyle}>
      <p css={titleStyle}>- Emotion -</p>
      <SButton>FIGHT!!</SButton>
    </div>
  );
};

const SButton = styled.button`
  background-color: #abedd8;
  border: none;
  padding: 8px;
  border-radius: 8px;
  &:hover {
    background-color: #46cdcf;
    color: #fff;
    cursor: pointer;
  }
`;

```

# おまけ
[Tailwindcss](https://tailwindcss.com/)

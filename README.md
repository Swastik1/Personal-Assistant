# Personal-Assistant
This is a progressive web app made with Sass.

Here is the Sass code which i converted to main.css using Live Sass Compiler :

------------------ CODE ------------------------

@import url("https://fonts.googleapis.com/css?family=Montserrat&display=swap");
$colors: (
  primary: #482a2a,
  primary-light: lighten(#005dff, 40%),
  primary-dark: darken(#005dff, 40%),
  accent: #fff6bb
);

$padding: 15px;
$borders: 15px;

@function color($color-name) {
  @return map-get($map: $colors, $key: $color-name);
}

$desktop: 840px;

@mixin desktop {
  @media (min-width: #{$desktop}) {
    @content;
  }
}

body,
html {
  height: 100%;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  margin: 0;
  #bg {
    clip-path: polygon(100% 0, 100% 82%, 45% 100%, 0 100%, 0 0);
    background-color: color(primary);
    width: 100%;
    height: 100%;
    position: absolute;
    z-index: -1;

    @include desktop() {
      clip-path: polygon(0 0, 75% 0, 55% 100%, 0% 100%);
    }
  }

  header a {
    color: #fff;
    text-decoration: none;
    padding: $padding;
    display: block;
    text-transform: uppercase;
  }
}

main {
  @include desktop() {
    display: grid;
    grid-template-columns: 50% auto;
    grid-template-areas: "primary card";
  }

  section#card {
    background: #fff;
    padding: 20px;
    margin: 1em auto;
    border-radius: $borders;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
    width: 80%;

    @include desktop() {
      grid-area: card;
      height: fit-content;
      align-self: center;
      margin: 1em;
    }

    ul {
      list-style-type: none;
      margin: 0;
      padding: 0;

      li {
        margin-bottom: 10px;

        span {
          position: absolute;
          width: 30px;
          height: 30px;
          background-color: color(primary-light);
          border-radius: 50%;
          margin-right: 10px;
        }

        strong {
          display: inline-block;
          margin-left: max($numbers: 40px);
          margin-top: 10px;
        }
      }
    }
  }
  section#primary {
    color: #fff;
    padding: $padding;
    text-align: center;

    @include desktop() {
      grid-area: primary;
      text-align: left;
      margin: 4em 0 0 4em;
    }

    h1 {
      font-size: 3em;
      margin-top: 10px;
      text-transform: uppercase;

      @include desktop() {
        width: 30%;
        font-size: 4em;
        line-height: 0.9em;
      }
    }

    p {
      font-size: 1.4em;
    }

    a {
      color: color(primary-dark);
      border-radius: $borders;
      text-decoration: none;
      text-transform: uppercase;
      font-weight: bold;
      background-color: color(accent);
      display: block;
      text-align: center;
      margin: 50px auto 0 auto;
      padding: $padding;

      @include desktop() {
        display: inline-block;
        padding: $padding $padding * 4;
      }
    }
  }
}


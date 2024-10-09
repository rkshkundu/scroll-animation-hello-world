    <section class="top test"></section>
    <section class="text-animation">
      <div class="placeholder-overlap">
        <span class="round-white"></span>
        <h2 class="title">Hello World</h2>
      </div>
      <div class="placeholder"></div>
    </section>
    <section class="bottom test"></section>

let $parent = document.querySelector(".text-animation");
let $child = $parent.querySelector(".placeholder-overlap");
let $roundWhite = $parent.querySelector(".round-white");

const windowHeight = window.innerHeight;
const windowWidth = window.innerWidth;
const scaleAmount = (windowWidth / 100) * 2.2;

console.log(scaleAmount);

function handleScroll() {
  let parentTop = $parent.getBoundingClientRect().top || 0;
  //   console.log(
  //     parentTop,
  //     "parentTop",
  //     -parentTop - windowHeight,
  //     windowHeight,
  //     -parentTop - windowHeight > windowHeight
  //   );

  if (-2 * windowHeight < parentTop && parentTop < 0) {
    scaleSize = (-parentTop / (2 * windowHeight)) * (windowWidth / 50 + 5);
    $roundWhite.style.transform = `scale(${scaleSize > 1 ? scaleSize : 1})`;
  }

  if (-parentTop - windowHeight > windowHeight) {
    parentTop = 2 * windowHeight + parentTop;
  } else {
    parentTop = parentTop >= 0 ? parentTop : 0;
  }
  $child.style.transform = `translate(0, ${parentTop}px)`;
}
document.addEventListener("scroll", handleScroll);
$child.style.transform = `translate(0, ${
  $parent.getBoundingClientRect().top || 0
}px)`;


* {
  margin: 0;
  padding: 0;
}
.test {
  height: 600px;
}
.top {
  background: red;
}
.bottom {
  background: yellow;
}
.placeholder {
  height: 300vh;
}
.placeholder-overlap {
  display: flex;
  align-items: center;
  position: fixed;
  top: 0;
  width: 100%;
  height: 100vh;
  background: black;
  overflow: hidden;
}
.round-white {
  display: inline-block;
  width: 100px;
  height: 100px;
  background: #fff;
  border-radius: 50%;
}
.title {
    font-size: 10vw;
    mix-blend-mode: difference;
    color: #fff;
}
https://jsfiddle.net/tpm7jkf3/
https://jsfiddle.net/tpm7jkf3/1/

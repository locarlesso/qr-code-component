# Frontend Mentor - QR code component solution
![](./screenshot(iPad).png)

This is a solution to the [QR code component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/qr-code-component-iux_sIO_H). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Built with

- Just plain old semantic HTML and CSS

## What I learned 

### Using [``<figure>``](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/figure) and [``<figcaption>``](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/figcaption)

```
<figure>
  <img title="QR Code" alt="WWW.FrontendMentor.IO">
  <figcaption>
    <p><b class="slogan">[brief attention-grabbing description]</b></p>
    <p>[extended description]</p>
  </figcaption>
</figure>
```
#### Accessibility Considerations
Most browsers will still use the figcaption as the acessible name for the figure. Which in this case I don't think is ideal, but is not a big deal. 

Besides, I don't think there's a way to avoid it. I could apply `aria-label="QR Code"` to the figure, but this seems excessive and would cause unnecessary repetition in Chrome. (see [short note on figure and figcaption](https://html5accessibility.com/stuff/2022/08/25/short-note-on-figure-and-figcaption/) for additional context)

---

### Centering a Specific Child with Siblings

**To [truly center](https://chrisbracco.com/css-truly-center-a-single-child-element-horizontally-when-siblings-are-present/) the card vertically, I used his top and bottom siblings as spacers:**

```
body {
    min-height: 100vh;
    min-height: 100dvh;
    display: flex;
    flex-direction: column;
}

body::before {
    content: "";
}

body::before,
footer {
    flex-grow: 1;
    flex-basis: 0;
}
```

#### Why Flex Instead of Grid?
I had to adapt Chris's (Truly Center) [solution](https://chrisbracco.com/css-truly-center-a-single-child-element-horizontally-when-siblings-are-present/#:~:text=center%3B%0A%7D-,CSS%20grid,-The%20above%20solutions) and use flex instead of grid because I wanted the top spacer to fully colapse on narrow viewports and the `fr` unit was making it keep the same height that the bottom spacer. ([because 1fr is equivalent to minmax(auto, 1fr)](https://stackoverflow.com/questions/52861086/why-does-minmax0-1fr-work-for-long-elements-while-1fr-doesnt#:~:text=Because%201fr%20is%20equivalent%20to%20minmax(auto%2C%201fr))) 

Although... there's a hack to make the grid version to work in the same way, using height instead of min-height. The container will overflow, but it's not apparent.

 Equally, the [flex](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#:~:text=a%20valid%20value%20for%20%3Cflex%2Dgrow%3E%3A%20then%20the%20shorthand%20expands%20to%20flex%3A%20%3Cflex%2Dgrow%3E%201%200.)`:1` shorthand also doesn't work with `min-height`.  (Because [CSS flex-basis: 0% has different behaviour to flex-basis: 0px](https://stackoverflow.com/questions/63475073/css-flex-basis-0-has-different-behaviour-to-flex-basis-0px))

 ---

## Useful resources

- [4.8.4.4 Requirements for providing text to act as an alternative for images](https://html.spec.whatwg.org/multipage/images.html#alt)

- [short note on figure and figcaption](https://html5accessibility.com/stuff/2022/08/25/short-note-on-figure-and-figcaption/)

- [The problem with 100vh](https://youtu.be/veEqYQlfNx8?t=120)

- [CSS “truly center” a single child element horizontally when siblings are present](https://chrisbracco.com/css-truly-center-a-single-child-element-horizontally-when-siblings-are-present/)

- [Quick Tip: Rounded Corners Done Right](https://webdesign.tutsplus.com/tutorials/quick-tip-rounded-corners-done-right--webdesign-7127)


## Links

- Solution URL: https://www.frontendmentor.io/solutions/a-valid-case-for-using-elements-as-spacers-h5J7XMrZzS

- Live Site URL: https://locarlesso.github.io/qr-code-component

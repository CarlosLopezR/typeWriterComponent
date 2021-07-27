# typeWriterComponent by Carlos Lopez
Hello guys, I created  this multine typeWriter in React fully user customizable! It was fun. I want to share so you dont have to go through this fun mess! If you can make it better make sure to share your improvements!:D


# Import into any of your classes

```Javascript
import TypeWrite from "./components/TypeWriter"; 
```


# Component Parameters:

```Javascript
         <TypeWrite
          text="Hello LinkedIn Community, while doing this great personal project, i encountered the need of creating this special component. Since there is alot of work            into it, i think its great to share what i have created so you dont go through this mess by yourself!@@@ :D" 
          x="60"
          y="50"
          fontSize="24"
          hexColor="FFFFFF"
        />
```

# Component Code:
```Javascript
import react, { useState, useEffect } from "react";

const TypeWrite = ({ text, x, y, fontSize, hexColor }) => {
  let mainArray = [];
  const [WordsTempContainer, AllocateWords] = useState([]);

  useEffect(() => {
    AllocateWords(genArrayofWords(text));
  }, []);

  function CountCharacters(text) {
    return text.length;
  }

  function genArrayofWords(source) {
    let ArrayContainer = source.split(" ");
    return ArrayContainer;
  }
  let k = 6;
  let z = 1;

  for (let i = 0; i < WordsTempContainer.length; i += k) {
    mainArray.push(WordsTempContainer.slice(i, i + k));
  }

  function incrementOverTime() {
    return z++;
  }

  const typeWriterCss = (subItem, oT) => ({
    textAlign: `center`,
    fontSize: `${fontSize}px`,
    color: `#${hexColor}`,
    fontWeight: `300`,
    margin: `0 auto`,
    fontFamily: `'Courier New', monospace`,
    whiteSpace: `nowrap`,
    overflow: `hidden`,
    width: `26em`,
    animation: `typeWriteAnim 1s steps(${CountCharacters(
      subItem
    )}) ${oT}s 1 normal both`,
  });

  const positionAbsoluteCss = {
    position: `absolute`,
    top: `${y}%`,
    left: `${x}%`,
  };

  const listOfNestedItems = mainArray.map((nestedItem, index) => (
    <div
      style={typeWriterCss(nestedItem.join(" "), incrementOverTime())}
      key={index}
    >
      {nestedItem.join(" ")}
    </div>
  ));

  const test = console.log(text.split(" ").join(" "));

  return <div style={positionAbsoluteCss}>{listOfNestedItems}</div>;
};

export default TypeWrite;

```

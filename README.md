# js::bind
The js::bind library is an header only library for [Emscripten](http:://www.emscripten.org/), to easily bind any C++ function, member function or lambdas as a Javascript callable callback.

## Easy to use

```cpp

  using namespace std;
  using std::placeholders;
  using emscripten::val;

  val::global("document")["body"].set("innerHTML", "<button id=\"clickme_btn\">Click me</button>");
  auto clickme_btn = val::global("document").call<val>("getElementById", string("clickme_btn"));

  auto onclick = [](val event){ cout << "hello world ! " << endl; };
  clickme_btn.set("onclick", js::bind(onclick, _1));
```

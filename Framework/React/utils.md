## ✅ 페이지 이동마다 맨 위로 자동 포커스
```js
//ScroolToTop
import { useEffect } from "react";
import { useLocation } from "react-router-dom";

function ScrollToTop() {
  const { pathname } = useLocation();

  useEffect(() => {
    window.scrollTo(0, 0);
  }, [pathname]);

  return null;
}

export default ScrollToTop;

//App.jsx 라우팅
<ScrollToTop />
      <Routes>
      </Routes>
```

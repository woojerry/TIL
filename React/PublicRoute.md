```jsx
import { useEffect } from "react";
import { Route, Redirect } from "react-router-dom";
import { useDispatch, useSelector } from "react-redux";

import { RootState } from "modules";
import { userCheck } from "modules/user";
import { Header } from "components";

interface RouteProps {
  component: React.FC;
  path: string;
  exact: boolean;
}

//These routes can be accessed before login into the App

const PublicRoute = ({ exact, path, component: Component }: RouteProps) => {
  const dispatch = useDispatch();
  const { loginSuccess } = useSelector((state: RootState) => state.user);

  useEffect(() => {
    dispatch(userCheck());
  }, [dispatch]);
  console.log(loginSuccess);
  return loginSuccess ? (
    <Redirect to="/" />
  ) : (
    <Route
      exact={exact}
      path={path}
      render={() => {
        if (path === "/")
          return (
            <>
              <Header />
              <Component />
            </>
          );
        return <Component />;
      }}
    />
  );
};

export default PublicRoute;

```

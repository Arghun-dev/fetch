# fetch

To fetch data using `fecth` do this

in class based components you should always fetch data in `componentDidmount` but I always use functional components so I have to fetch data in `useEffect`

```
import React, { useState, useEffect } from "react";

const FetchData = () => {
  const [posts, setPosts] = useState([]);
  const [loading, setLoading] = useState(false);
  useEffect(() => {
    setLoading(true);
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((data) => data.json())
      .then((data) => {
        setPosts(data);
        setLoading(false);
      });
  }, []);

  return (
    <>
      {loading ? (
        <div>Loading...</div>
      ) : (
        <div>
          {posts.map((post) => {
            return (
              <div key={post.id}>
                <h4>{post.title}</h4>
                <p>{post.body}</p>
              </div>
            );
          })}
        </div>
      )}
    </>
  );
};

export default FetchData;
```

The class based component is exactly just like this, but you have to fetch data inside `componentDidmount` life cycle method in class components

# N + 1 problem

### What is N+1 problem?

It's a issue when an application makes N+1 database queries when it could have achieved  the same result with just one query. This can cause unnecessary slow response times, affecting the application's performance.

Examples:

```php
public function index()
{
	$posts = Post::all();

	foreach ($posts as $post) {
		$comments = $posts->comments;
	}

	return view('posts.index', ['comments' => $comments]);
}

```

In this code, the initial query returns all the posts, but for each post, Laravel makes a new query to the database to retrieve the comments on that post. If you have 100 posts, this will result in 1 query to retrieve the posts and 100 additional queries to retrieve the comments, i.e. 101 queries in total. Inside the loop, for each post, Laravel will make a separate query to retrieve the comments related to that post. This is because the relationship between Post and Comment is probably a `hasMany` relationship.

```sql
First query to retrieve all posts from posts table

SELECT * FROM posts;

Aditional queries to retrieve all comments `from` each post

SELECT * FROM comments WHERE post_id = 1; 
SELECT * FROM comments WHERE post_id = 2; 
SELECT * FROM comments WHERE post_id = 3; 
... 
SELECT * FROM comments WHERE post_id = 100;
```

### How to avoid this problem?

This problem can be solved by using `eager loading` with `with` method. It will load all the comments once, instead of making each query for each post.

```php
public function index()
{
	$posts = Post::with('comments')->get();

	return view('posts.index', ['posts' => $posts]);
}
```

The query will be like this:

```sql
SELECT * FROM posts;
SELECT * FROM comments WHERE post_id IN (1, 2, 3, ..., N);
```


_References:_

https://medium.com/doctolib/understanding-and-fixing-n-1-query-30623109fe89

https://planetscale.com/blog/what-is-n-1-query-problem-and-how-to-solve-it

https://dev.to/jackynote/solving-the-notorious-n1-problem-optimizing-database-queries-for-java-backend-developers-2o0p
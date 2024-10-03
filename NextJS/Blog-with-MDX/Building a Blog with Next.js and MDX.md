Getting Started:

Head to terminal and create a project folder.
Create a new nextjs project by running the following command:
```shell
npx create-next-app@latest
```

 install `next-mdx-remote` by running the following command:
```shell
npm install next-mdx-remote
```

Building the Blog Post Page
First lets look at the blog post page. I know it might feel odd not starting with the `index` page...but stick with it.

To establish the blog post page, first, set up the **routing**. 
1. Inside the `app` directory, create a directory named '`blog`'. 
2. Inside '`blog`', make a folder named '`[slug]`'. 
3. And within the '`[slug]`' folder, create a file named '`page.tsx`'. 

The structure should resemble `app/blog/[slug]/page.tsx`, where '`[slug]`' serves as the dynamic segment for blog posts. 
```
- app
	- blog
		- [slug]
			- page.tsx
```

To start, let's create a basic markdown file for testing. Organise it in a 'markdown' folder, designed for storing all markdown blog post files.
A Docker Image to run Reveal Presentations
===========================================

## Why ?
If you want to *build a [reveal.js](https://github.com/hakimel/reveal.js) presentation*, using *external markdown files* but you don't want to **install and configure a complex embedded Node.js application** : all you need is this docker image !

## How ?

###	Build the image :
`docker build -t docker-reveal-[VERSION]--build-arg REVEAL_VERSION=[VERSION] .` 
Replace [VERSION] with the desired [reveal.js release](https://github.com/hakimel/reveal.js/releases) for example 3.3.0

###	Run the image :
`docker run -d  -p 8001:8000 -v [LOCAL_DIRECTORY_PATH]:/prez --name docker-prez docker-reveal`
Replace [LOCAL_DIRECTORY_PATH] with the absolute path of the directory containing the Reveal presentation

###	The content of the reveal presentation :

1.	an index.html with an html section as :
				`<section data-markdown="slides/dockprez.md"  
                         data-separator="^\n\n\n"  
                         data-separator-vertical="^\n\n">
                </section>`
2.	a "slides" directory
3.	your markdown file under the "slides" directory
4.  don't forget the reveal configuration using the  following dependencies 
			`Reveal.initialize({
                controls: true,
                progress: true,
                history: true,
                center: true,
           
                // Optional libraries used to extend on reveal.js
                dependencies: [
                    { src: 'lib/js/classList.js', condition: function() { return !document.body.classList; } },
                    { src: 'plugin/markdown/marked.js', condition: function() { return !!document.querySelector( '[data-markdown]' ); } },
                    { src: 'plugin/markdown/markdown.js', condition: function() { return !!document.querySelector( '[data-markdown]' ); } }
                ]
            });`
> Of course, you needs docker installed on your machine !
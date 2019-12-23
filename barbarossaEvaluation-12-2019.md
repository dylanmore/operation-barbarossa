## Barbarossa Project Review

Site publication: <http://barbarossa.newtfire.org/>

GitHub: <https://github.com/dylanmore/operation-barbarossa>

Developers:
* Dylan More: @dylanmore
* Matt Nowakowski: @mattnowakowski

Date of Evaluation: 2019-12-22

Evaluated by: @ebeshero @ksd32 


### General 

Overall, team Barbarossa did well with exploring its research questions and presenting its results. We particularly like how you've introduced Operation Barbarossa and taken some care to identify and show the leaders of both the German and Soviet forces, and share some background videos for context. We don't see any licensing of your materials on the site, so we suggest adding a [Creative Commons License](https://creativecommons.org/licenses/) if you want to tell others it's okay with you to share your code as long as you're cited. We do, however, think we should be seeing more detailed explanation of your project's research methods on the site.

### Research questions

The project's research question was about whether there is a correlation between certain battles of Operation Barbarossa and the casualities recorded. Your "Results" page indicates that there was no correlation between the two. What could use more discussion on the site is *how* you made this determination, in a way that responds to the specific data that we see when we read the pages linked from your Timeline. If you're sharing this work professionally, we recommend that you expand this explanation, and the standard way is to add a page called "Methods" to the site. You could be linking such a page to your GitHub repo, and share some discussion of the kinds of source materials you worked with, as well as how you marked up and studied the data from these sources to come to the conclusion that you did. You could also be discussing the difficulties of assessing the available data, as you presented to us in class. We know you can do this because we've discussed the project with you, but those arriving to this site as an information resource will have questions that you can't answer in person, so you should write up your methods and point to your project's GitHub repo with direct links so people can see something of the markup you did. (Currently the only links to your project GitHub are indirect, because you've provided them only for your personal repos on your "About Us" page.)

### Technologies

We like how you developed your Timeline to link to pages about each battle. That was a clever design strategy you came up with early in the project and it works effectively here. The SVG is also well designed to be prominent and represent the numbers of casualties on each distinct battle. It's a little difficult to think of all of the battles as a collection, though, to consider how they compare and contrast, without a summary page that shows us all the battles at once. A summary graph for all the battles is probably an SVG you can make very easily based on the distinct ones you produced for each battle. We were surprised not to see any XSLT on your site, and we recognize that both team members were out of class on some crucial days when we were going over XSLT to SVG. Because there aren't a lot of files documenting your methods, we're guessing that you pulled your data with XPath to plot it. The advantage of doing that work in XSLT is that it can serve as documentation and store those XPath expressions for you together with any comments you want to preserve about it. (For example, did you try to pull casualty numbers with the same attribute values for `@unit`? Considering your [Relax-NG schema for the source materials](https://github.com/dylanmore/operation-barbarossa/blob/master/project-schema/sourceschema.rnc) that would make sense, but you should really be telling us about that work somewhere on the site and in some record of your processing code. Even if that was simply drawing SVG based on XPath results that you took by hand, you want to be documenting the XPath expressions somewhere in a prominent place. One of the key aspects of doing research scientifically is being able to hand your materials to other researchers so that they can test your methods and see if they can duplicate your results.
   

### GitHub

Your GitHub repo is well organized and provides access to your markup, schema, website development, and source materials for the project. What's missing is much record of your processing of your data. [The commit history](https://github.com/dylanmore/operation-barbarossa/graphs/contributors) is sparse--only 19 commits across this semester, which is a lot fewer than most projects we see, but the work appears to be evenly portioned between the team partners.

###  “UX”: User Experience and Site Interface
The graphics and colors were mostly well chosen, and we like the red and white on black background that you applied, both for contrast and suitability for the topic. There's a problem with the color of links: blue (for active links) and purple (for followed links) isn't easy to read against that black background, so we'd recommend changing those, probably to a couple of shades of red that pop a little better on the site display. The timeline is holding the "heart" of the project where the most detailed commentary on the battles may be found, and that's easily navigable and simply designed with HTML and CSS. (Simply designed is good, because it can be easy to modify later if you decide to add more entries or detail. 

However, we're getting [some unhappy reports from the w3c Validator](https://validator.w3.org/nu/?doc=http%3A%2F%2Fbarbarossa.newtfire.org%2F), which basically checks if your whole page design is valid with current HTML 5 standards and accessible for people with all kinds of web browsers on a variety of systems (including braille browsers). Your site is pretty clean, but there's a major problem on the index page that you can easily fix. \ The problem is pretty simple, and it's to do with your inclusion of the entire [timeline.html](https://github.com/dylanmore/operation-barbarossa/blob/master/website/timeline.html) as an SSI, because that file is a complete HTML file on its own. That should just be a snippet of code that *completes* your HTML page, so you just want to cut out everything in timeline.html that wouldn't fit inside a `<body>` element. (Right now it's turning out as basically two HTML root elements on one page, so the page isn't valid and sending up a lot of errors from the w3c validator.)

You have some flexboxes coded in your CSS, but these aren't being applied where they're needed on index.html. Take a look at the main page of the site, and see how much wider the title bar is from the rest of the page? With a little tinkering, you can fix that with flexbox containers to hold the image in check so it's the same width as the rest of the page. Think of what element you're using as a container that includes both the title bar and the main content. Usually that's the `<body>` element--but you need to repair that nyway because you currently have two `<body>` elements (which isn't valid HTML). So if you fix that, you'd have one `<body>` to wrap the whole page that will be your flex container, and then your nav bar in its `<header>` element can be balanced against something that wraps the rest of your content (including the timeline). We like `<div>` or `<section>` elements for that kind of work. So then you'd have two "boxes" you can flex vertically in a column, and the flex containment can control the width of that title bar. 

Generally you've aligned center all the body text of your site, which is a little strange in the world of the web (it tends to look like student work when everything is aligned center). To spruce up the site's professional appearance we'd recommend left-aligning your body text since that's ordinarily the way we read body paragraphs, and reserve centering just for headings.  

### Closing Comments
Operation Barbarossa turned out as an attractive and informative web resource over the course of a single semester, and we hope you'll continue to refine it to enhance its professional qualities as a serious resource for history fans and even for educational use. To do that, you'll want to write up more documentation about your methods--the most serious area that needs improvement here, besides the "small stuff" that is fixing the HTML validation problems on the index page. Good work this semester, and we hope you'll stay in touch and continue developing this fine project!

# BrickIt LEGO Mosaic Generator Javascript Library
Javascript library for uploading an image and getting a LEGO-ized version of it and an optimized instruction manual almost instantly.

I will be adding the core javascript library I wrote as well as some documentation on how to use it, but for now, feel free to check out www.brickit.co, all the source code is very easy to find and not minified.

###Regarding the "Parting-Out Algorithm" I Created

I created www.BrickIt.co using just jQuery and HTML5's Canvas element to do this and actually got a great algorithm for parting things out I came up with when I was 20 (3 years ago), it's wicked fast (like 1024 pegs x 1024 pegs image in less than 10 seconds) and as optimal as any complex optimization problem attempt. Everyone wayy over complicates it. I think the parting out results speaks for themselves.

It's simple. Given a set of brick dimensions (2x4, 2x3, 1x6, 2x2, 1x4, 1x3, 1x2, 1x1). Start out with the highest priority piece (2x4) in the top left corner and work your way from left to right, top to bottom, checking:
Does this piece fit here (doesn't exceed the boundary)
Has any piece already been placed here before (If I were to place this piece here, would it overlap 
Are all colors the same for the pegs that that piece would take up if it were to be placed there
If so, place it, if not, move to the left 1 (or start a new row) etc.
Go through the entire image trying to place the top priority piece, then repeat starting in the top left corner for the second highest priority piece, etc.

Once you realize you can place a piece, draw it with the borders, otherwise it'd be really hard to figure out where are the borders are supposed to go once you are done.

Theoretically, you could save maybe 1% of pieces or costs if you started your optimizations in other places other than the top left corner, but you would also spend millions of times longer processing every possible starting location and sprawl pattern for a 1% improvement gain.

How I have this implemented is ridiculously easy as well, just have two matrices, one to indicate the color index of a particular peg, one to keep track if that peg has a piece placed on it or not, and then I guess you have to have the matrix representing your actual image as well.

I'll try and add my BrickIt project to github soon, none of the source code is obfuscated though so feel free to look through it (literally just vanilla javascript, jQuery and HTML5 canvas) - I was going to try and turn it into a business or sell it but it's been years now.

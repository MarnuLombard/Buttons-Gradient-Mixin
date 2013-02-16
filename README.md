#SCSS & Compass mixin for generating background-image gradients

###[See example here](http://rawgithub.com/MarnuLombard/Buttons-Gradient-Mixin/blob/master/test.html)

(*Provided by rawgithub.com*)

### Syntax

**Called by @include gradient(color);**

For instance *@include gradient(#ccc);* outputs:

	.class {
		-webkit-box-shadow: 0 2px 5px #6b6b6b, inset 0 1px 0 white;
		-moz-box-shadow: 0 2px 5px #6b6b6b, inset 0 1px 0 white;
		box-shadow: 0 2px 5px #6b6b6b, inset 0 1px 0 white;
		border: 1px solid #666666;
		background-image: -webkit-gradient(linear, 50% 0%, 50% 100%, color-stop(0%, #cccccc), 
						   color-stop(100%, #8c8c8c));
		background-image: -webkit-linear-gradient(top, #cccccc, #8c8c8c);
		background-image: -moz-linear-gradient(top, #cccccc, #8c8c8c);
		background-image: -o-linear-gradient(top, #cccccc, #8c8c8c);
		background-image: linear-gradient(top, #cccccc, #8c8c8c); 
	}
	.class:active,
	.class:hover,
	.class:focus {
		background-image: -webkit-gradient(linear, 50% 0%, 50% 100%, color-stop(0%, #b3b3b3), 
						   color-stop(100%, #666666));
		background-image: -webkit-linear-gradient(top, #b3b3b3, #666666);
		background-image: -moz-linear-gradient(top, #b3b3b3, #666666);
		background-image: -o-linear-gradient(top, #b3b3b3, #666666);
		background-image: linear-gradient(top, #b3b3b3, #666666); }
	.class:active,
	.class:focus {
		-webkit-box-shadow: 0 2px 5px #6b6b6b, inset 0 0 20px #666666;
		-moz-box-shadow: 0 2px 5px #6b6b6b, inset 0 0 20px #666666;
		box-shadow: 0 2px 5px #6b6b6b, inset 0 0 20px #666666; 
	}

### Variables
There are several `if.. else if.. else ` conditions, all based on lightness of input.
**For instance:** 

	lightness($color) > 50% { @if lightness($color) < 10% {
		@include background-image( 
			linear-gradient( 
				top, adjust-hue(lighten($color, 25%),4%), $color 
			)
		);
	}
	
	@else if lightness($color) > 90%{		
		@include background-image( 
			linear-gradient( 
				top, $color, darken($color, 10%) 
			) 
		);
	}
	
	@else {		
		@include background-image( 
			linear-gradient( 
				top, $color, darken($color, 25%) 
			) 
		);
	}// gradient
 
See the source-code for more.
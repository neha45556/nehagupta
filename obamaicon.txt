from PIL import Image 

darkBlue = (0, 51, 76)
red = (217, 26, 33)
lightBlue = (112, 150, 158)
yellow = (252, 227, 166)

im = Image.open("sf.jpg")
image_pixels = im.getdata()
img_list_data = list(image_pixels)


def colorize(img_list_data):
	picture =[]
	for pixel in image_pixels:
		red = pixel[0]
		green = pixel[1]
		blue = pixel[2]
		intensity = red + green + blue  
		if intensity < 182:
			picture.append(darkBlue)
		elif intensity  < 364:
			picture.append(red)
		elif intensity <564:
			picture.append(lightBlue)
		else :
			picture.append(yellow)
	return picture

data_colorized = colorize(img_list_data)
new_image = Image.new(im.mode, im.size)
new_image.putdata(data_colorized)
new_image.show()
new_image.save("output", "jpeg")

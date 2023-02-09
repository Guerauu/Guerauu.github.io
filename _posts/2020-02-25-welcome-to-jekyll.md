---
layout: post
---


You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].


[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

'''python3

#!/usr/bin/env python3

# this script translates bad usb ducky scripts to german keyboard layout
# all props go to u/felice-el-chillo, just removed the hardcoded filename to argument


import sys

de_lang    = '''1234567890qwertzuiopasdfghjkl<yxcvbnm,.-QWERTZUIOPASDFGHJKL>YXCVBNM;:_[]|{}\\+#!$%&/()=?`*" '''
ducky_lang = '''1234567890qwertyuiopasdfghjkl;zxcvbnm,.ßQWERTYUIOPASDFGHJKL:ZXCVBNMöÖ?ü+’Ü*#`§!$%/-)=´_<(@ '''

file_name = sys.argv[1]
file = open(file_name, "r")
lines = []

for line in file:
    if line[0:6] == "STRING":
        line_string = "STRING " 
        for line_character in line[7:]:
            if line_character == "\"":
                line_string+="@"
            else:
                line_string += de_lang[ducky_lang.find(line_character)]
        lines.append(line_string)
    else:
        lines.append(line)

with open((file_name[0:len(file_name)-4]+"_DE.txt"), 'w') as f:
    f.write('\n'.join(lines))

'''

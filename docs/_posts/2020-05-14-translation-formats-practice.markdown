---
layout: post
title:  "File formats in CAT tools 2 - direct editing"
date:   2020-05-11 13:50:25 +0200
categories: jekyll update
---

**Warning:** Blog post under construction, still needs some editing.

*This is a series of blog posts on file formats used by CAT (Computer-assisted translation) programs for storing translation data. Their aim is to share some knowledge which should allow us to tame our CAT tools better. Or to become independent from their whims.*

*This post discusses ways of editing file types often used by translators - XML files and archives - without actually using a CAT tool. If you want to learn about these files first see [Part 1]({{ site.baseurl }}{% link _posts/2020-05-11-translation-formats-intro.markdown %}).*

## Prerequisites

In order to tinker with translation files, you will need a few programs:

- A **text editor** for opening files (on Windows, you can use the default Notepad or the free [Notepad++](https://notepad-plus-plus.org/))
- A program for **opening zip archives** (on Windows, you can use the free [7Zip](https://www.7-zip.org/download.html))
- A **CAT tool** of your choice (e.g. the free [OmegaT](https://omegat.org/download))

I have prepared some example files for us. You can download them [from here].

# Case 1 - enabling source editing in Trados

Let's say you obtain a Trados package for translation. However, you notice that the PM must have failed to prepare the file, since some text in the source segment is mangled, translation memory shows very few matches for it etc. Source editing is turned off, so you cannot fix this directly in Trados. There is no way to contact the agency during the weekend, your deadline is on Monday morning. It's a nightmare. What do you do?

Answer: dive under the hood! Let's unlock source editing before we actually work on the file in Trados.

*Warning: although the workaround seems justified in this case, some PMs might not be happy with changing source text, especially if they use some automatic way of keeping track of files (changed source might confuse some systems). Better try to ask beforehand. Although if the goal is to deliver the translated file, and not keep the intermediate .sdlproj, this workaround should leave no traces and be fine.*

1. Copy the *.sdlppx* file to a separate folder
2. Extract the files to this location
3. Go into the resulting unpacked archive (folder with the same name, but without the .zip extension) and open the *example.sdlxliff* file
4. Change (?)
5. Save the file
6. Select the folder with the unpacked archive and compress it to a .zip file
8. Change the extension from *.zip* back to *.sdlppx*

# Case 2 - directly editing the source (the working, but risky way)

Let's say we have the same problem as before. But this time, we might be using a different CAT tool which does not allow source editing at all. Our only solution is to edit the source text in the XML file directly.

**Warning**: this method involves editing XML as if it were plaintext. Normally, this is discouraged, since the XML has more structure to it and making reckless changes can lead to file corruption. However, you should be OK if you follow some simple rules. Check the Appendix for details. 

1. Same as steps 1-3 from Case 1
2. (?)

## Conclusion

As we can see, the common formats used in translation are more accessible than we thought. We can edit both the settings and the actual content to some degree. Text editors and zip unpackers fit most of our needs.

However, you have probably noticed the warnings. As the classics say, with great power comes great responsibility... if we are not careful while playing with our files, our troubleshooting attempts might actually cause us more grief. What if we could somehow get the best of both worlds - 

## Appendix

# safe XML editing

I have added a disclaimer that recklessly editing XML might corrupt your files. However, it is not as scary as it sounds. You just need to follow a few simple rules.

1. Use an editor which does not change file content/encoding (most of them, including Notepad++, are OK)
2. Make sure you only edit text
3. Do not change any content inside tags
4. Do not add the <, > or & characters
5. Verify the result by opening it in your CAT tool

```xml
<tag namespace:id="3" translate='yes'>Translatable text</tag>
```
 

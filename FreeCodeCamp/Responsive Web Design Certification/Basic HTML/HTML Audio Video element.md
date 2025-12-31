- The `audio` and `video` elements allow you to add sound and video content to your HTML documents. The `audio` element supports popular audio formats like mp3, wav, and ogg. The `video` element supports mp4, ogg, and webm formats.
- To include audio content on your web page, you can use the `audio` element with the `src` attribute pointing to the location of your audio file.
- `<audio src="https://cdn.freecodecamp.org/curriculum/js-music-player/cruising-for-a-musing.mp3" controls></audio>` : need to include `controls` for the audio player to appear in the webpage
- Apart from the `src` and `controls` attributes, there are several other attributes that enhance the functionality of the `audio` element. The `loop` attribute is a boolean attribute that makes the audio replay continuously.
- Another attribute you can use is the `muted` attribute. When present in the `audio` element, this boolean attribute will start the audio in a muted state. Here's an example of using the `muted` attribute.
- When it comes to audio file types, there are differences in which browsers support which type. To accommodate this, you can use `source` elements inside the `audio` element and the browser will select the first source that it understands. Here's an example of using multiple `source` elements for an `audio` element:
  `<audio controls>`
  `<source src="audio.ogg" type="audio/ogg" />`
  `<source src="audio.wav" type="audio/wav" />`
  `<source src="audio.mp3" type="audio/mpeg" />`
  `</audio>`
- All the attributes we have learned so far are also supported in the `video` element. Here's an example of using a `video` element with the `loop`, `controls`, and `muted` attributes.
- Add the `autoplay` attribute to the opening `video` tag so the video plays automatically. To interact with the example, you will need to enable the interactive editor.
- The `width` attribute is being used here to make the video smaller and fit better in the preview window. You will learn more about the `width` attribute in future lessons.
  `<video`
  `src="https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4"`
  `loop`
  `controls`
  `muted`
  `width="400"`
  `autoplay`
  `poster="https://peach.blender.org/wp-content/uploads/title_anouncement.jpg?x11217"`
  `></video>`
- For the `src`, or source attribute, we are using a video called "Big Buck Bunny" from archive.org. If you wanted to display an image while the video is downloading, you can use the `poster` attribute. This attribute is not available for `audio` elements and is unique to the `video` element. Here's an example of using the `poster` attribute with content provided by peach.blender.org.
- 
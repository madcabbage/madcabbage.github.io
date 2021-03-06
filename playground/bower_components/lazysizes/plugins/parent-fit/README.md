#lazySizes parent fit extension

The parent fit plugin extends the ``data-sizes="auto"`` feature to also calculate the right ``sizes`` for ``object-fit: contain|cover`` image elements as also **height** ( and width) constrained image elements in general.

##Usage

For this to work properly the physical aspect-ratio of the image candidates need to be calculable. To do so at least one of the image candidates inside the ``srcset`` attribute also need to include a **h** (height) descriptor.

###object-fit: contain|cover usage

Simply include this plugin, combine your width descriptors with height descriptors and use ``object-fit``.

```html
<img data-srcset="http://lorempixel.com/400/800/people/6/ 400w 800h,
	http://lorempixel.com/300/600/people/6/ 300w 600h,
	http://lorempixel.com/200/400/people/6/ 200w 400h"
	 data-sizes="auto"
	 class="lazyload"
	 style="width: 400px; height: 400px; object-fit: contain;" />

<img data-srcset="http://lorempixel.com/800/400/people/9/ 800w 400h,
	http://lorempixel.com/600/300/people/9/ 600w 300h,
	http://lorempixel.com/400/200/people/9/ 400w 200h"
	 data-sizes="auto"
	 class="lazyload"
	 style="width: 400px; height: 400px; object-fit: cover;" />
```

###[data-parent-fit="contain|cover|width"] usage

Due to the fact, that object-fit isn't supported in IE11. This plugin also supports calculating height and width constrained images based on the parent element.

To do so include this plugin, combine your width descriptors with height descriptors and add the attribute ``data-parent-fit`` with either ``"contain"`` or ``"cover"`` as the keyword.

```html
<div style="width: 400px; height: 400px; display: flex; align-items: center; justify-content: center;">
	<img data-srcset="http://lorempixel.com/400/800/people/6/ 400w 800h,
		http://lorempixel.com/300/600/people/6/ 300w 600h,
		http://lorempixel.com/200/400/people/6/ 200w 400h"
		 data-sizes="auto"
		 class="lazyload"
		 data-parent-fit="contain"
		 style="max-width: 100%; max-height: 100%;" />
</div>
```

In case the *width* keyword is used, lazySizes simply takes the width of the parent container instead of the ``img`` element itself. In this case a **h** descriptor isn't necessary.

Note: This plugin should be also added, if you use the [bgset plugin](../bgset/) in combination with ``data-sizes="auto"`` and ``background-size: cover|contain``.

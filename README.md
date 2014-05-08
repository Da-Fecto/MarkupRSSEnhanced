# ProcessWire Markup RSS Enhanced Module

This Module is the enhanced version of Ryan's Markup RSS Module.

Given a PageArray of pages, this module will render an RSS feed from them.
This is intended to be used directly from a template file.

### Usage

    /**
     * Defaults
     *
     */
    $rss = $modules->get("MarkupRSSEnhanced");
    $rss->title = 'Title of the RSS feed.';
    $rss->description = 'Description of the RSS feed.';
    $rss->copyright = "©2014;
    $rss->ttl = '60'; // TTL time to life/refresh, 60 minutes default

    /**
     * settings for closure
     *
     * If an image is used for closure, specify the required width & height.
     * If an other format is specified, say MP3, there's no need to set them.
     */
    $rss->width = 400;
    $rss->height = 300;
    /* resize the image till the sides or the top/bottom is reached */
    $rss->boundingbox = 1; // 1 or 0

    /**
     * settings for closure
     *
     * If an image is used for closure, specify the required width & height.
     * If an other format is specified, say MP3, there's no need to set them
     */
    $rss->itemTitleField = 'title';
    $rss->itemDescriptionField = 'summary';
    $rss->itemDescriptionLength = 1024;
    // enclosure
    $rss->itemEnclosureField = 'file'; // image/file field
    $rss->itemLinkField = 'fieldname'; // leave empty to use Page url
    $rss->itemDateField = 'created';

    $items = $pages->find("limit=10, sort=-modified"); // or any pages you want

    $rss->render($items);

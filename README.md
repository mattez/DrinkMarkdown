DrinkMarkdown
=============

Extended PHP Markdown parser tuned for usage in ATK14 projects. It's built on Michel Fortin's PHP Markdown Extra.

Originally it was developed for the project "Doctor Ink" (shortly "Drink").

Beware! It is in alpha state. It has some interconnections to the ATK14 Framework thus it can't be easily used in other projects.

Installation
------------

Just use the Composer:

    cd path/to/your/atk14/project/
    composer require atk14/drink-markdown dev-master

Optionaly you can link (or copy & edit) helpers to your project.

    ln -s ../../vendor/atk14/drink-markdown/src/helpers/smarty/block.markdown.php app/helpers/
    ln -s ../../vendor/atk14/drink-markdown/src/helpers/smarty/block.safe_markdown.php app/helpers/
    ln -s ../../vendor/atk14/drink-markdown/src/helpers/smarty/modifier.markdown.php app/helpers/
    ln -s ../../vendor/atk14/drink-markdown/src/helpers/smarty/modifier.safe_markdown.php app/helpers/

Usage
-----

    $dm = new DrinkMarkdown(array(
      "table_class" => "table", // the CSS class for tables, default is "table table-bordered table-hover"
      "html_purification_enabled" => true, // default is true
      "temp_dir" => "/path/to/temp", // default is constant TEMP or sys_get_temp_dir()
    ));

    $html = $dm->transform($markdown);

Usage in a ATK14 template
-------------------------

If you have a trusted content:

    {$text|markdown nofilter} {* or *}
    {!$text|markdown}

If you have an insecure content, e.g. a comment from a user

    {$comment|safe_markdown nofilter} {* or *}
    {!$comment|safe_markdown}

License
-------

DrinkMarkdown is free software distributed [under the terms of the MIT license](http://www.opensource.org/licenses/mit-license)

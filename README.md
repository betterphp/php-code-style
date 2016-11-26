# PHP Code Style
This is the ruleset that should be used in any of my PHP projects

Add the repo to composer
~~~
"repositories": [
	{
		"type": "vcs",
		"url": "https://github.com/betterphp/php-code-style.git"
	}
]
~~~

Then add the dev dependency
~~~
"require-dev": {
	"betterphp/php-code-style": "dev-master",
	"squizlabs/php_codesniffer": "~2"
}
~~~

Run `composer update` then run phpcs from the command line
~~~
./vendor/bin/phpcs -p --standard=./vendor/betterphp/php-code-style/Standard/ruleset.xml .
~~~

Alternatively include the rules in a custom ruleset.xml file, useful to add file exclusions or make tweaks etc.
~~~
<?xml version="1.0"?>
<ruleset name="example-project-style">
	<description>Example Project Code Style</description>
	<exclude-pattern type="relative">^node_modules/*</exclude-pattern>
	<exclude-pattern type="relative">^.git/*</exclude-pattern>
	<exclude-pattern type="relative">^vendor/*</exclude-pattern>

	<rule ref="vendor/dataplan/code-standard/Standard" />

	<!-- PHPUnis uses epcial function comments -->
	<rule ref="Standard.Commenting.FunctionComment">
		<exclude-pattern>*/tests/*</exclude-pattern>
	</rule>

	<!-- Not too bothered about spacing and full stops -->
	<rule ref="Standard.Commenting.FunctionComment.SpacingAfterParamType"><severity>0</severity></rule>
	<rule ref="Standard.Commenting.FunctionComment.SpacingAfterParamName"><severity>0</severity></rule>
	<rule ref="Standard.Commenting.FunctionComment.ThrowsNoFullStop"><severity>0</severity></rule>
	<rule ref="Standard.Commenting.FunctionComment.ParamCommentFullStop"><severity>0</severity></rule>
</ruleset>
~~~

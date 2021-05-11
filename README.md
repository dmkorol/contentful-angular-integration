# Contentful Angular integration

Idea: Have i18n module with mixed translations. Some static, some dynamic with storing at Contentful.
Implementation: Patched i18n module with FrontEnd editing-highliting-tracking missed translations

Scenarios:
1. Content manager open qa server and can change content without FE
2. FE can check matching keys on UI and trace path where it cames from
3. QA can trace path for missing translations

# Implementation

1. Create test project with i18n TranslationModule
2. Create lazy loading modules
3. Create translations in en.json / fr.json
4. Create translations in Contentful
5. Load translations from Contentful
6. Create mock Nodejs Api return text-labels
7. Angular HTTP Interceptor
8. Chrome Extention
9. Missing translations

## Angular HTTP Interceptor
1. Patch all http/fetch/XHTMLRequest to add hidden UTF-8 symbols for tracking
2. Put into session storage hashmap with relation 'utf8 key':'endpoint url + path'

## Chrome Extention
1. Parse all text nodes, check first N symbols - match hidden utf8
2. Implement tooltip on hover with info
3. Add button possition absolute with manual update for parsing "Parse DOM Tree"
4. Add settings with interval checkings (setInterval or on requiest or manual)
5. Intorduce sidebar with info

## Missing translations
1. Collect into localStorage missing translations - page, date, count
2. If it is possible collect Component Tree info from Angular

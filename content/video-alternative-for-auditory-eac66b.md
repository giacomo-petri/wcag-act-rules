---
title: "video element auditory content has accessible alternative"
permalink: /standards-guidelines/act/rules/video-alternative-for-auditory-eac66b/
ref: /standards-guidelines/act/rules/video-alternative-for-auditory-eac66b/
lang: en
github:
  repository: w3c/wcag-act-rules
  path: content/video-alternative-for-auditory-eac66b.md
footer: |
  <p><strong>Date:</strong> Updated 22 October 2021</p>
  <p><strong>Authors:</strong> <a href="https://www.linkedin.com/in/brianbors/">Brian Bors</a>, <a href="https://github.com/wilcofiers">Wilco Fiers</a>.</p>
  <p>This rule was written in the <a href="https://w3.org/community/act-r/">ACT Rules community group</a>. It is written as part of the EU-funded <a href="https://www.w3.org/WAI/about/projects/wai-tools/">WAI-Tools Project</a>.</p>
proposed: true
rule_meta:
  id: eac66b
  name: "`video` element auditory content has accessible alternative"
  rule_type: composite
  description: |
    This rule checks that `video` elements have an alternative for information conveyed through audio.
  accessibility_requirements:
    'wcag20:1.2.2':
      forConformance: true
      failed: not satisfied
      passed: further testing needed
      inapplicable: further testing needed
    'wcag-technique:G87':
      forConformance: false
      failed: not satisfied
      passed: further testing needed
      inapplicable: further testing needed
    'wcag-technique:G93':
      forConformance: false
      failed: not satisfied
      passed: further testing needed
      inapplicable: further testing needed
    'wcag-technique:H95':
      forConformance: false
      failed: not satisfied
      passed: further testing needed
      inapplicable: further testing needed
  input_aspects:
    - ab4d13
    - f51b46
  last_modified: 22 October 2021
  scs_tested:
    - handle: Captions (Prerecorded)
      num: 1.2.2
      level: A
---

{::options toc_levels="2" /}
{::nomarkdown}
{% include toc.html type="start" title="Page Contents" %}
{:/}

- Table of Content placeholder
{:toc}

{::nomarkdown}
{% include toc.html type="end" %}
{:/}

## Applicability

This rule applies to every [non-streaming](#non-streaming-media-element) `video` element that is [visible][], where the video contains audio.

## Expectation

For each test target, the [outcome](#outcome) of at least one of the following rules is passed:

- [`Video` Element Content Is Media Alternative For Text](https://act-rules.github.io/rules/ab4d13)
- [`Video` Element Auditory Content Has Captions](https://act-rules.github.io/rules/f51b46)

## Assumptions

- This rule assumes that the video element is used to play synchronized media (video with audio), and that there is a mechanism to start the media.
- This rule assumes that the language of each test target can be correctly determined (either programmatically or by analyzing the content), and sufficiently understood.

## Accessibility Support

There are no major accessibility support issues known for this rule.

## Background

- [Understanding Success Criterion 1.2.2: Captions (Prerecorded)](https://www.w3.org/WAI/WCAG21/Understanding/captions-prerecorded)
- [G93: Providing open (always visible) captions](https://www.w3.org/WAI/WCAG21/Techniques/general/G93)
- [G87: Providing closed captions](https://www.w3.org/WAI/WCAG21/Techniques/general/G87)
- [H95: Using the track element to provide captions](https://www.w3.org/WAI/WCAG21/Techniques/html/H95)

## Test Cases

### Passed

#### Passed Example 1

A video element with an associated track element that contains captions for all the audio.

```html
<html lang="en">
	<video src="/test-assets/perspective-video/perspective-video.mp4" controls>
		<track src="/test-assets/perspective-video/perspective-caption.vtt" kind="captions" />
	</video>
</html>
```

#### Passed Example 2

A video element that describes some of the text on the same page. The text on the page labels the video as an alternative.

```html
<html lang="en">
	<p>
		Web Accessibility Perspectives: Keyboard Accessibility. Not being able to use your computer because your mouse
		doesn't work, is frustrating. Many people use only the keyboard to navigate websites. Either through preference or
		circumstance. This is solved by keyboard compatibility. Keyboard compatibility is described in WCAG. See the video
		below to watch the same information again in video form.
	</p>
	<video src="/test-assets/perspective-video/perspective-video.mp4" controls></video>
</html>
```

### Failed

#### Failed Example 1

A video element without any form of captions.

```html
<html lang="en">
	<video src="/test-assets/perspective-video/perspective-video.mp4" controls></video>
</html>
```

#### Failed Example 2

A video element that describes some of the text on the same page. The video contains more information than the text does.

```html
<html lang="en">
	<p>
		Not being able to use your computer because your mouse doesn't work, is frustrating. Either through preference or
		circumstance. This is solved by keyboard compatibility. Keyboard compatibility is described in WCAG. See the video
		below to watch the same information again in video form.
	</p>
	<video src="/test-assets/perspective-video/perspective-video.mp4" controls></video>
</html>
```

### Inapplicable

#### Inapplicable Example 1

A video element that is not [visible][].

```html
<html lang="en">
	<video src="/test-assets/perspective-video/perspective-video.mp4" controls style="display: none;"></video>
</html>
```

#### Inapplicable Example 2

A video element without audio.

```html
<html lang="en">
	<video src="/test-assets/perspective-video/perspective-video-silent.mp4" controls></video>
</html>
```

## Glossary

### Non-streaming media element {#non-streaming-media-element}

A _non-streaming media element_ is an [HTML Media Element](https://html.spec.whatwg.org/multipage/media.html#htmlmediaelement) for which the `duration` property is not 0.

### Outcome {#outcome}

An _outcome_ is a conclusion that comes from evaluating an ACT Rule on a [test subject](https://www.w3.org/TR/act-rules-format/#test-subject) or one of its constituent [test target](https://www.w3.org/TR/act-rules-format/#test-target). An outcome can be one of the three following types:

- **Inapplicable:** No part of the test subject matches the applicability
- **Passed:** A [test target](https://www.w3.org/TR/act-rules-format/#test-target) meets all expectations
- **Failed:** A [test target](https://www.w3.org/TR/act-rules-format/#test-target) does not meet all expectations

**Note:** A rule has one `passed` or `failed` outcome for every [test target](https://www.w3.org/TR/act-rules-format/#test-target). When there are no test targets the rule has one `inapplicable` outcome. This means that each [test subject](https://www.w3.org/TR/act-rules-format/#test-subject) will have one or more outcomes.

**Note:** Implementations using the [EARL10-Schema](https://www.w3.org/TR/EARL10-Schema/) can express the outcome with the [outcome property](https://www.w3.org/TR/EARL10-Schema/#outcome). In addition to `passed`, `failed` and `inapplicable`, EARL 1.0 also defined an `incomplete` outcome. While this cannot be the outcome of an ACT Rule when applied in its entirety, it often happens that rules are only partially evaluated. For example, when applicability was automated, but the expectations have to be evaluated manually. Such "interim" results can be expressed with the `incomplete` outcome.

### Visible {#visible}

Content perceivable through sight.

Content is considered _visible_ if making it fully transparent would result in a difference in the pixels rendered for any part of the document that is currently within the viewport or can be brought into the viewport via scrolling.

[Content is defined in WCAG](https://www.w3.org/TR/WCAG21/#dfn-content).

For more details, see [examples of visible](https://act-rules.github.io/pages/examples/visible/).

{% include_relative implementations/eac66b.md %}

## Changelog

This is the first version of this ACT rule.

[visible]: #visible 'Definition of visible'
---

title: "Publications"

description: "Publications by Faisal Farhan on medical imaging, physiological monitoring, biomedical signal analysis, computer-aided diagnosis and computer vision."

layout: gridlay

permalink: /p/

---

{%- comment -%}

Output per year, drawn at build time so it costs no library and no script.

Bar heights are relative to the busiest year; each bar links to its heading.

{%- endcomment -%}

{%- assign peak = 0 -%}

{%- assign shown = 0 -%}

{%- assign dated = 0 -%}

{%- for y in site.data.years -%}

  {%- assign n = site.publications | where: "year", y.year | size -%}

  {%- if n > 0 -%}

    {%- assign shown = shown | plus: 1 -%}

    {%- assign dated = dated | plus: n -%}

    {%- if n > peak -%}{%- assign peak = n -%}{%- endif -%}

  {%- endif -%}

{%- endfor -%}

{%- comment -%}anything without a year is a working document{%- endcomment -%}

{%- assign undated = site.publications | size | minus: dated -%}

{%- if undated > 0 -%}

  {%- assign shown = shown | plus: 1 -%}

  {%- if undated > peak -%}{%- assign peak = undated -%}{%- endif -%}

{%- endif -%}

{%- assign step = 34 -%}

{%- assign chartw = shown | times: step -%}

{%- assign ordered = site.data.years | reverse -%}

# Publications

<div markdown="0" class="pub-chart-wrap">

<svg markdown="0" class="pub-chart" width="{{ chartw }}" height="118" viewBox="0 0 {{ chartw }} 118" role="img" aria-label="Publications per year, peaking at {{ peak }}">

{% assign i = 0 %}{% for y in ordered %}{% assign n = site.publications | where: "year", y.year | size %}{% if n > 0 %}{% assign h = n | times: 88 | divided_by: peak %}{% assign x = i | times: step %}<a href="#{{ y.year }}"><title>{{ y.year }}: {{ n }} publication{% if n != 1 %}s{% endif %}</title><rect class="pub-chart-hit" x="{{ x }}" y="0" width="{{ step }}" height="118"></rect><text class="pub-chart-n" x="{{ x | plus: 17 }}" y="{{ 96 | minus: h }}">{{ n }}</text><rect class="pub-chart-bar" x="{{ x | plus: 4 }}" y="{{ 100 | minus: h }}" width="{{ step | minus: 8 }}" height="{{ h }}" rx="2"></rect><text class="pub-chart-y" x="{{ x | plus: 17 }}" y="114">{{ y.year }}</text></a>{% assign i = i | plus: 1 %}{% endif %}{% endfor %}{% if undated > 0 %}{% assign h = undated | times: 88 | divided_by: peak %}{% assign x = i | times: step %}<a href="#working-documents"><title>Working documents: {{ undated }} publication{% if undated != 1 %}s{% endif %}</title><rect class="pub-chart-hit" x="{{ x }}" y="0" width="{{ step }}" height="118"></rect><text class="pub-chart-n" x="{{ x | plus: 17 }}" y="{{ 96 | minus: h }}">{{ undated }}</text><rect class="pub-chart-bar pub-chart-wd" x="{{ x | plus: 4 }}" y="{{ 100 | minus: h }}" width="{{ step | minus: 8 }}" height="{{ h }}" rx="2"></rect><text class="pub-chart-y" x="{{ x | plus: 17 }}" y="114">n/a</text></a>{% endif %}

</svg>

</div>

<div id="pub-filters">

<div class="filter-group">

  <span class="filter-label">Search</span>

  <input type="search" id="pub-search" placeholder="title, author, venue, year…" aria-label="Search publications" autocomplete="off" />

</div>

<div class="filter-group">

  <span class="filter-label">Type</span>

  <button class="filter-btn active" data-filter="all">All</button>

  <button class="filter-btn" data-filter="conference">Conference</button>

  <button class="filter-btn" data-filter="journal">Journal</button>

  <!-- <button class="filter-btn" data-filter="poster">Poster</button> -->

  <button class="filter-btn" data-filter="preprint">Preprint</button>

  <button class="filter-btn" data-filter="thesis">Thesis</button>

</div>

<div class="filter-group">
  <span class="filter-label">Methods</span>
  <button type="button" class="filter-btn active" data-filter="all">All</button>
  <button type="button" class="filter-btn" data-filter="machine-learning">Machine learning</button>
  <button type="button" class="filter-btn" data-filter="deep-learning">Deep learning</button>
  <button type="button" class="filter-btn" data-filter="signal-processing">Signal processing</button>
  <button type="button" class="filter-btn" data-filter="image-processing">Image processing</button>
  <button type="button" class="filter-btn" data-filter="feature-selection">Feature selection</button>
  <button type="button" class="filter-btn" data-filter="optimization">Optimization</button>
  <button type="button" class="filter-btn" data-filter="optical-measurement">Optical measurement</button>
</div>

<div class="filter-group">
  <span class="filter-label">Topics</span>
  <button type="button" class="filter-btn active" data-filter="all">All</button>
  <button type="button" class="filter-btn" data-filter="medical-imaging">Medical imaging</button>
  <button type="button" class="filter-btn" data-filter="physiological-monitoring">Physiological monitoring</button>
  <button type="button" class="filter-btn" data-filter="biomedical-signal-analysis">Biomedical signal analysis</button>
  <button type="button" class="filter-btn" data-filter="computer-aided-diagnosis">Computer-aided diagnosis</button>
  <button type="button" class="filter-btn" data-filter="computer-vision-applications">Computer vision applications</button>
</div>

<div class="filter-group">

  <button class="filter-btn" id="reset-filters">Reset filters</button>

  <span id="pub-count"></span>

</div>

</div>

{% assign yeartest = true %}

{% for publi in site.publications %}

{% if publi.year %}{% else %}

{% assign yeartest = false %}

{% endif %}

{% endfor %}

{% if yeartest == false %}

## Working documents

{% endif %}

{% for publi in site.publications %}

{% assign pdfpresent = false %}

{% if publi.pdf %}

{% assign pdfpresent = true %}

{% assign pdffile = publi.pdf | append: ".pdf" %}

{% endif %}

{% if publi.year %}{% else %}

{% assign bibpresent = false %}

{% if publi.pdf %}

{% assign bibpresent = true %}

{% assign bibfile = publi.pdf | append: ".txt" %}

{% endif %}

{% assign tag_string = publi.tags | join: " " | downcase %}

{% assign search_string = publi.title | append: " " | append: publi.authors | append: " " | append: publi.display | append: " " | append: publi.year | append: " " | append: tag_string | downcase %}

<div class="well-sm publication-entry" data-tags="{{ tag_string | escape }}" data-search="{{ search_string | escape }}">

<ul class="flex-container">

<li class="flex-item1">

{% if publi.image %}

<img loading="lazy" src="{{ site.baseurl }}/p/{{ publi.image }}" alt="" class="img-responsive"/>

{% endif %}

</li>

<li class="flex-item2">

{% if publi.pdf %}<a href="{{ site.baseurl }}/p/{{ publi.pdf }}" target="_blank">{% endif %}<strong class="pub-title">{{ publi.title }}</strong>{% if publi.pdf %}</a>{% endif %} {% if publi.tags %}{% for tag in publi.tags %}<span class="pub-tag {{ tag | downcase }}">{{ tag }}</span>{% endfor %}{% endif %}<br/>

<span class="pub-authors">{{ publi.authors }}</span><br/>

<em class="pub-venue">{{ publi.display }}</em><br/>

{% if publi.abstract %}<a data-bs-toggle="collapse" href="#abstract-{{ publi.slug | default: publi.title | slugify }}" class="btn-abstract" style="text-decoration:none;color:#ebebeb;" role="button" aria-expanded="false" aria-controls="abstract-{{ publi.slug | default: publi.title | slugify }}">ABSTRACT</a>{% endif %}

{% if bibpresent == true %}<a data-bs-toggle="collapse" href="#{{publi.pdf}}2" class="btn-bib" style="text-decoration:none;color:#ebebeb;" role="button" aria-expanded="false" aria-controls="{{publi.pdf}}2">BIB</a>{% endif %}

{% if pdfpresent == true %}<a href="{{ site.baseurl }}/p/{{ pdffile }}" target="_blank"><button class="btn-pdf">PDF</button></a>{% endif %}

{% if publi.doi %}<a href="https://doi.org/{{ publi.doi }}" target="_blank"><button class="btn-doi">DOI</button></a>{% endif %}

{% if publi.arxiv %}<a href="https://arxiv.org/abs/{{ publi.arxiv }}" target="_blank"><button class="btn-arxiv">ARXIV</button></a>{% endif %}

{% if publi.code %}<a href="{{ publi.code }}" target="_blank"><button class="btn-code">CODE</button></a>{% endif %}

{% if publi.suppmat %}<a href="{{ publi.suppmat }}" target="_blank"><button class="btn-suppmat">SUPPLEMENT</button></a>{% endif %}

{% if publi.abstract %}

<div class="collapse" id="abstract-{{ publi.slug | default: publi.title | slugify }}"><div class="well-abstract">

{{publi.abstract}}

</div></div>

{% endif %}

{% if bibpresent == true %}

<div class="collapse" id="{{publi.pdf}}2"><div class="well-bib">

<button class="btn-copy" type="button">Copy</button>

<pre class="bib-text" data-src="{{site.baseurl}}/p/{{publi.pdf}}.txt"></pre>

</div></div>

{% endif %}

</li>

</ul>

</div>

{% endif %}

{% endfor %}

{% if site.group_pub_by_year == true %}{% else %}

## Journal papers and proceedings

{% endif %}

{% for myyear in site.data.years %}

{% assign yeartest = false %}

{% for publi in site.publications %}

{% if publi.year == myyear.year %}

{% assign yeartest = true %}

{% endif %}

{% endfor %}

{% if site.group_pub_by_year == true %}

{% if yeartest == true %}

## {{ myyear.year }}

{% endif %}

{% endif %}

{% for publi in site.publications %}

{% assign pdfpresent = false %}

{% if publi.pdf %}

{% assign pdfpresent = true %}

{% assign pdffile = publi.pdf | append: ".pdf" %}

{% endif %}

{% if publi.year == myyear.year %}

{% assign bibpresent = false %}

{% if publi.pdf %}

{% assign bibpresent = true %}

{% assign bibfile = publi.pdf | append: ".txt" %}

{% endif %}

{% assign tag_string = publi.tags | join: " " | downcase %}

{% assign search_string = publi.title | append: " " | append: publi.authors | append: " " | append: publi.display | append: " " | append: publi.year | append: " " | append: tag_string | downcase %}

<div class="well-sm publication-entry" data-tags="{{ tag_string | escape }}" data-search="{{ search_string | escape }}">

<ul class="flex-container">

<li class="flex-item1">

{% if publi.image %}

<img loading="lazy" src="{{ site.baseurl }}/p/{{ publi.image }}" alt="" class="img-responsive"/>

{% endif %}

</li>

<li class="flex-item2">

{% if publi.pdf %}<a href="{{ site.baseurl }}/p/{{ publi.pdf }}" target="_blank">{% endif %}<strong class="pub-title">{{ publi.title }}</strong>{% if publi.pdf %}</a>{% endif %} {% if publi.tags %}{% for tag in publi.tags %}<span class="pub-tag {{ tag | downcase }}">{{ tag }}</span>{% endfor %}{% endif %}<br />

<span class="pub-authors">{{ publi.authors }}</span><br />

<em class="pub-venue">{{ publi.display }}</em>{% if publi.year %} (<span class="pub-year">{{publi.year}}</span>){% endif %}<br/>

{% if publi.abstract %}<a data-bs-toggle="collapse" href="#abstract-{{ publi.slug | default: publi.title | slugify }}" class="btn-abstract" style="text-decoration:none;color:#ebebeb;" role="button" aria-expanded="false" aria-controls="abstract-{{ publi.slug | default: publi.title | slugify }}">ABSTRACT</a>{% endif %}

{% if bibpresent == true %}<a data-bs-toggle="collapse" href="#{{publi.pdf}}2" class="btn-bib" style="text-decoration:none;color:#ebebeb;" role="button" aria-expanded="false" aria-controls="{{publi.pdf}}2">BIB</a>{% endif %}

{% if pdfpresent == true %}<a href="{{ site.baseurl }}/p/{{ pdffile }}" target="_blank"><button class="btn-pdf">PDF</button></a>{% endif %}

{% if publi.doi %}<a href="https://doi.org/{{ publi.doi }}" target="_blank"><button class="btn-doi">DOI</button></a>{% endif %}

{% if publi.arxiv %}<a href="https://arxiv.org/abs/{{ publi.arxiv }}" target="_blank"><button class="btn-arxiv">ARXIV</button></a>{% endif %}

{% if publi.code %}<a href="{{ publi.code }}" target="_blank"><button class="btn-code">CODE</button></a>{% endif %}

{% if publi.suppmat %}<a href="{{ publi.suppmat }}" target="_blank"><button class="btn-suppmat">SUPPLEMENT</button></a>{% endif %}

{% if publi.abstract %}

<br/>

<div class="collapse" id="abstract-{{ publi.slug | default: publi.title | slugify }}"><div class="well-abstract">

{{publi.abstract}}

</div></div>

{% endif %}

{% if bibpresent == true %}

<div class="collapse" id="{{publi.pdf}}2"><div class="well-bib">

<button class="btn-copy" type="button">Copy</button>

<pre class="bib-text" data-src="{{site.baseurl}}/p/{{publi.pdf}}.txt"></pre>

</div></div>

{% endif %}

</li>

</ul>

</div>

{% endif %}

{% endfor %}

{% endfor %}

{% comment %}
Add a link to your own combined BibTeX file here when it is ready.
{% endcomment %}

<script>

(function () {

var groups = document.querySelectorAll('#pub-filters .filter-group');

var search = document.getElementById('pub-search');

// Abstracts are already in the page inside each entry, so searching them costs no extra

// bytes. Cache the plain text of every highlightable field once so a keystroke never has

// to walk the DOM. Each selector must wrap text only, since marking rewrites innerHTML.

var MARKABLE = '.pub-title, .pub-authors, .pub-venue, .pub-year, .pub-tag';

var entryData = new Map();

document.querySelectorAll('.publication-entry').forEach(function (entry) {

var abstractEl = entry.querySelector('.well-abstract');

entryData.set(entry, {

fields: Array.prototype.map.call(entry.querySelectorAll(MARKABLE), field),

abstract: abstractEl ? field(abstractEl) : null,

abstractLower: abstractEl ? abstractEl.textContent.toLowerCase() : ''

});

});

function field(el) { return { el: el, text: el.textContent, sig: '' }; }

function escapeRe(s) { return s.replace(/[.*+?^${}()|[\]\\]/g, '\\$&'); }

function escapeHtml(s) { return s.replace(/[&<>]/g, function (c) { return { '&': '&amp;', '<': '&lt;', '>': '&gt;' }[c]; }); }

function mark(f, terms) {
  var sig = terms.join('\u0000');
  if (f.sig === sig) return;
  f.sig = sig;
  if (!terms.length) { f.el.textContent = f.text; return; }
  var re = new RegExp(terms.map(escapeRe).join('|'), 'gi');
  var output = '';
  var cursor = 0;
  f.text.replace(re, function (match, offset) {
    output += escapeHtml(f.text.slice(cursor, offset));
    output += '<mark>' + escapeHtml(match) + '</mark>';
    cursor = offset + match.length;
    return match;
  });
  f.el.innerHTML = output + escapeHtml(f.text.slice(cursor));
}

// each group holds a Set of active filters; empty Set = "all"

var activeFilters = Array.from(groups).map(function () { return new Set(); });

function applyFilters() {

var required = [];

activeFilters.forEach(function (set) { set.forEach(function (f) { required.push(f); }); });

var terms = (search.value || '').trim().toLowerCase().split(/\s+/).filter(Boolean);

var entries = document.querySelectorAll('.publication-entry');

var visible = 0;

entries.forEach(function (entry) {

var tags = (entry.getAttribute('data-tags') || '').split(/\s+/).filter(Boolean);

var match = required.every(function (f) { return tags.indexOf(f) !== -1; });

var data = entryData.get(entry);

var fromAbstract = false;

if (match && terms.length) {

var haystack = entry.getAttribute('data-search') || '';

// all terms must appear, so "farhan perfusion" narrows rather than widens

match = terms.every(function (t) { return haystack.indexOf(t) !== -1 || data.abstractLower.indexOf(t) !== -1; });

// a term that only hit the abstract leaves no visible reason for the row,

// so open that abstract too

fromAbstract = match && terms.some(function (t) { return haystack.indexOf(t) === -1; });

}

var hits = (match && terms.length) ? terms : [];

data.fields.forEach(function (f) { mark(f, hits); });

if (data.abstract) {

mark(data.abstract, fromAbstract ? terms : []);

data.abstract.el.parentNode.classList.toggle('search-expanded', fromAbstract);

}

entry.classList.toggle('hidden', !match);

if (match) visible++;

});

var countEl = document.getElementById('pub-count');

if (countEl) countEl.textContent = visible + ' paper' + (visible !== 1 ? 's' : '');

document.querySelectorAll('h2').forEach(function (h2) {

var hasPaper = false;

var el = h2.nextElementSibling;

while (el && el.tagName !== 'H2') {

if (el.classList.contains('publication-entry') && !el.classList.contains('hidden')) { hasPaper = true; break; }

el = el.nextElementSibling;

}

h2.style.display = hasPaper ? '' : 'none';

});

}

// The address bar mirrors the current view, so a filtered or searched page can

// be shared or bookmarked. Filter names are unique across the three filter groups, so

// one tags= list is enough to restore them.

function syncUrl() {

var tags = [];

activeFilters.forEach(function (set) { set.forEach(function (f) { tags.push(f); }); });

var params = new URLSearchParams();

if (search.value.trim()) params.set('q', search.value.trim());

if (tags.length) params.set('tags', tags.join(','));

var query = params.toString();

// replace rather than push: typing must not bury the previous page in history

history.replaceState(null, '', query ? location.pathname + '?' + query : location.pathname);

}

function readUrl() {

var params = new URLSearchParams(location.search);

search.value = params.get('q') || '';

var wanted = (params.get('tags') || '').split(',').filter(Boolean);

wanted.forEach(function (f) {

var btn = document.querySelector('.filter-btn[data-filter="' + CSS.escape(f) + '"]');

if (!btn) return;                       // a filter that no longer exists is ignored

var group = btn.closest('.filter-group');

activeFilters[Array.prototype.indexOf.call(groups, group)].add(f);

btn.classList.add('active');

});

groups.forEach(function (group, i) { syncAllBtn(group, activeFilters[i]); });

}

function syncAllBtn(group, set) {

var allBtn = group.querySelector('.filter-btn[data-filter="all"]');

if (allBtn) allBtn.classList.toggle('active', set.size === 0);

}

groups.forEach(function (group, groupIndex) {

var set = activeFilters[groupIndex];

group.querySelectorAll('.filter-btn[data-filter]').forEach(function (btn) {

btn.addEventListener('click', function () {

var f = btn.getAttribute('data-filter');

if (f === 'all') {

set.clear();

group.querySelectorAll('.filter-btn[data-filter]').forEach(function (b) { b.classList.remove('active'); });

} else {

if (set.has(f)) {

set.delete(f);

btn.classList.remove('active');

} else {

set.add(f);

btn.classList.add('active');

}

}

syncAllBtn(group, set);

syncUrl();

applyFilters();

});

});

});

search.addEventListener('input', function () { syncUrl(); applyFilters(); });

document.getElementById('reset-filters').addEventListener('click', function () {

search.value = '';

groups.forEach(function (group, i) {

activeFilters[i].clear();

group.querySelectorAll('.filter-btn[data-filter]').forEach(function (btn) {

btn.classList.toggle('active', btn.getAttribute('data-filter') === 'all');

});

});

syncUrl();

applyFilters();

});

readUrl();

applyFilters();

})();

</script>

{% include bibtex.html %}

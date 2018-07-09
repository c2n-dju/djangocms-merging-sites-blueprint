# djangocms-merging-sites-blueprint
A blueprint for merging several django-cms sites under the same url

To build a large lab site for about 30 different teams, the decentralized way, using different SITE_ID
has a number of advantages.
- simpler editing authorization administration
- simpler cross-linking:
    choosing between 30 sites and then between 50 pages is possible
    with current link menus, choosing between 1500 pages is impossible
- independent 1-process uwsgi tasks

For editing, SITE_ID=1 corresponds to https://edit-www.lab.science/,
SITE_ID=2 corresponds to https://edit-team-a.lab.science/,
SITE_ID=3 corresponds to https://edit-team-b.lab.science/, etc.

The standard way to publish the edited content is to use several sites
http://www.lab.science/,  http://team-a.lab.science/,  http://team-b.lab.science/, etc.

The aim of this project is to merge the edited content under an unique umbrella, with the URLs
http://www.lab.science/, http://www.lab.science/teams/a, , http://www.lab.science/teams/b, etc.

Unfortunately, django-cms is using `get_current_site()` in several methods instead of using a `Site` argument. 

# CodingStandardsForDjango

This is an initial thought and serves as a guideline for your Django application.

We will follow pep8 and Google python style guideline as standard.

<h2>Naming Convention</h2>
<ul>
  <li>Use meaningful names</li>
  <li>Function and variable names in snake_case</li>
  <li>Classname in PascalCase</li>
  <li>Constants snake_case capitalized</li>
</ul>
<h2>Indentation/Space</h2>
<ul>
  <li>Use 4 spaces for indentation(Python 3 disallows mixing the use of tabs and spaces for indentation)</li>
  <li>Separate top level function and classes with two blank lines</li>
  <li>Separate method definition inside class by one line</li>
  <li>Maximum length of line should be less than 80 characters</li>
  <li>There should be no trailing white spaces</li>
</ul>
<h2>Imports</h2>
<ul>
  <li>Import from Python standard library(1st)</li>
  <li>Import from core Django(2nd)</li>
  <li>Import from 3rd party vendor(3rd)</li>
  <li>Import from Django Apps(4th)(Current Project)</li>
  <li>Avoid import *</li>
</ul>
<h2>Migrations</h2>
  <ul>
    <li>Do not modify the files created by makemigration command(do not add custom sql command)</li>
    <li>Place custom sql command if needed in a separate file and do not mix it with the auto generated files from makemigration command</li>
    <li>Forward and backward migration work only on auto generated files by makemigration command</li>
    <li>Not all migration can be reversed</li>
    <li>Add — database=<dbConfigName> always in your migration</li>
  </ul>
 <h3>Forward Migration</h3>
 <ul>
   <li>python manage.py migrate appname 0002 — settings=project.settings.<Env> — database=<dbConfigName></li>
   <li>python manage.py migrate appname 0003 — settings=project.settings.<Env> — database=<dbConfigName></li>
   <li>Suppose it added all the migration 0001.py , 0002.py , 0003.py , 0004.py</li>
 </ul>
 <h3>Backward Migration</h3>
 <ul>
   <li>(Remove New migrations -0002.py , 0003.py , 0004.py)</li>
   <li>python manage.py migrate appname 0001 — settings=project.settings.<Env> — database=<dbConfigName></li>
 </ul>
<h2>Response Status</h2>
<p>Response message with status codes</p>
<pre><code>{</br>
    ‘status’:’success|error’,</br>
    ‘data’:{</br>
             'result':{} || [] , ''</br>
            }, #one level</br>
    ‘meta’:{} #any meta information that you want to pass</br>
}</pre></code>
<ul>

  <li>200 OK — Success — GET/PUT — return resource/status message</li>
  <li>201 Created — Success — POST — provide status message or return newly created object</li>
  <li>204 No Content — Success — DELETE</li>
  <li>304 Unchanged — Redirect — ALL — Indicates no changes since last request</li>
  <li>400 Bad Request — Failure — GET/PUT/POST — invalid request, return error messages</li>
  <li>401 Unauthorized — Failure — ALL — missing credentials/Authentication required</li>
  <li>403 Forbidden — Failure — ALL — restricted content</li>
  <li>404 Not Found — Failure — Resource not found</li>
  <li>405 Method Not Allowed Failure — Failure — ALL — An invalid HTTP method was attempted</li>
<h2>App Structure</h2>
<pre><code>project/
    gitignore
    README.md
    docs/
    requirements/
        local.txt
        qa.txt
        prod.txt
        base.txt
    project/
        settings/
            base.py //copy of original settings.py
            qa.py
            local.py
            prod.py
        urls.py
        wsgi.py
        settings_default.py //renamed settings->settings_default
    app1/
    app2/
        v1/
            api.py // entry point , not much logic
            service.py // all business logic
            util.py // any helper
        test/
        migrations/
        admin.py
        models.py
        apps.py
        urls.py
        views.py
    utils/
        service/
        helper/</code></pre>
<h2>Tools/Extra</h2>
<ul>
  <li>Code Quality — flake8</li>
  <li>Environment Manager — venv</li>
  <li>Documentation — Swagger</li>
  <li>Testing — pytest</li>
  <li>IDE — sublime,vim,pycharm</li>
  <li>Debug — pdb</li>

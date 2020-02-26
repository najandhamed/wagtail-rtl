# wagtail-rtl (version 2.8)
This is the style sheet Wagtail Admin based on Bootstrap 4.x

Step 1: Create Core application.
  for windows:
    py manage.py startapp core
  for other OS:
    python manage.py startapp core

Step 2: Create a file named 'wagtail_hooks.py' within Core folder that you had made in Step 1.

Step 3: Inside 'wagtail_hooks.py' write code below:
<pre>
  from django.utils.html import format_html
  from django.templatetags.static import static
  from wagtail.core import hooks

  @hooks.register("insert_global_admin_css")
  def global_admin_css():
      """Add /static/css/custom.css to the admin."""
      return format_html(
          '<link rel="stylesheet" href="{}">',
          static("css/admin.css")
      )
</pre>

Step 4: Create 'admin.css' located in 'project_name\project_name\static\css\admin.css' .
Step 5: Paste all of style sheets there.
Step 6: enjoy.

In case of custom javascript file you can add the code below under Admin Css's file:

  @hooks.register('insert_global_admin_js')
  def global_admin_js():
    return format_html(
        '<script src="{}"></script>',
        static("/js/admin.js")
    )

Then located 'admin.js' in 'project_name\project_name\static\js\admin.js' . 

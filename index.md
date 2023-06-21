<html>
  <head>
    <title>AAJE Posts</title>
    <link rel="stylesheet" type="text/css" href="css/index.css">
    
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/tablesorter@2.31.3/dist/js/jquery.tablesorter.combined.min.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tablesorter@2.31.3/dist/css/theme.bootstrap_4.min.css">
    <script>
    $(document).ready(function() {
      $(".myTable").tablesorter();
    });
    </script>

<script>
  document.addEventListener('click', function(event) {
    if (event.target.classList.contains('toggle-comments-btn')) {
      var button = event.target;
      var row = button.closest('.row');
      var commentsRow = row.nextElementSibling;
      commentsRow.classList.toggle('hidden');
    }
  });
</script>

<script>
  var searchInput = document.getElementById('search-input');
  var rows = document.getElementsByClassName('row');

  searchInput.addEventListener('input', function() {
    var searchTerm = this.value.trim().toLowerCase();

    for (var i = 0; i < rows.length; i++) {
      var row = rows[i];
      var postText = row.querySelector('.post-text').textContent.toLowerCase();

      if (postText.includes(searchTerm)) {
        row.style.display = 'table-row';
      } else {
        row.style.display = 'none';
      }
    }
  });
</script>




    
  </head>
  <body>
    <main>
      <h1>AAJE Posts</h1>
      
      <input type="text" id="search-input" placeholder="Search...">
      
      <table class="myTable">
        <thead>
          <tr>
            <!-- <th class="header">Compagnie</th> -->
            <th class="header">Author</th>
            <th class="header">Date</th>
            <th class="header">Text</th>
            <th class="header">Tags</th>
          </tr>
        </thead>
        <tbody>
          {% for post in site.data.aaje_posts %}
              <tr class="row">
                <td>{{ post.Author }}</td>
                <td>{{ post.PostDate }}</td>
                <td>{{ post.PostText }}</td>
                <td><button class="toggle-comments-btn">
                  {{ post.Comments.size }}
                  {% if post.Comments.size > 1 %}
                    commentaires
                  {% else %}
                    commentaire
                  {% endif %}
                </button></td>
              </tr>
              <tr class="comments-row hidden">
                <td colspan="4">
                  <table class="myTable">
                    <thead>
                      <tr>
                        <th class="header">Comment Author</th>
                        <th class="header">Comment Date</th>
                        <th class="header">Comment Text</th>
                      </tr>
                    </thead>
                    <tbody>
                      {% for comment in post.Comments %}
                      <tr>
                        <td>{{ comment.Author }}</td>
                        <td>{{ comment.CommentDate }}</td>
                        <td>{{ comment.CommentText }}</td>
                      </tr>
                      {% endfor %}
                    </tbody>
                  </table>
                </td>
              </tr>          
          {% endfor %}
        </tbody>
      </table>
        
    </main>
  </body>
</html>

<html>
  <head>
    <title>AAJE Posts</title>
    <style>
      .wrapper {
        max-width: 90%;
        margin-right: auto;
        margin-left: auto;
        padding-right: 30px;
        padding-left: 30px;
      }
      
      table {
        border-collapse: collapse;
        width: 100%;
      }

      th, td {
        text-align: left;
        padding: 8px;
      }

      th {
        cursor: pointer;
      }

      th:hover {
        background-color: #ddd;
      }
      
.hidden {
  display: none;
}


    </style>

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





    
  </head>
  <body>
    <main>
      <h1>AAJE Posts</h1>

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
                <td><button class="toggle-comments-btn">Toggle Comments</button></td>
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

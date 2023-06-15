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
    </style>

    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/tablesorter@2.31.3/dist/js/jquery.tablesorter.combined.min.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tablesorter@2.31.3/dist/css/theme.bootstrap_4.min.css">
    <script>
    $(document).ready(function() {
      console.log("test");
      $(".myTable").tablesorter();
    });
    </script>
    
  </head>
  <body>
    <main>
      <h1>AAJE Posts</h1>

      {% for post in site.data.aaje_posts %}
      <div class="post">
        <h2>{{ post.PostId }}</h2>
        <p>{{ post.Author }}</p>
        <p>{{ post.PostDate }}</p>
        <p>{{ post.PostText }}</p>
        <div class="comments">
          {% for comment in post.Comments %}
            <div class="comment">
              <p><strong>{{ comment.Author }}</strong></p>
              <p>{{ comment.CommentDate }}</p>
              <p>{{ comment.CommentText }}</p>
            </div>
          {% endfor %}
        </div>
      </div>
      {% endfor %}
        
    </main>
  </body>
</html>

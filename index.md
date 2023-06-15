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
      $(".myTable").tablesorter();
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
              <tr>
                <td>{{ post.Author }}</td>
                <td>{{ post.PostDate }}</td>
                <td>{{ post.PostText }}</td>
                <td></td>
              </tr>
          {% endfor %}
        </tbody>
      </table>
        
    </main>
  </body>
</html>

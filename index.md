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
  height: 0;
  overflow: hidden;
  transition: height 0.3s ease-in-out;
}

.comments-row.visible {
  height: auto;
  transition: height 0.3s ease-in-out;
}

@keyframes rollDown {
  0% {
    transform: translateY(-100%);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

.roll-down-animation {
  animation: rollDown 0.3s ease-in-out;
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
  document.addEventListener('DOMContentLoaded', function() {
    var commentsRows = document.getElementsByClassName('comments-row');
    for (var i = 0; i < commentsRows.length; i++) {
      commentsRows[i].classList.add('hidden');
    }
  });

  document.addEventListener('click', function(event) {
    if (event.target.classList.contains('toggle-comments-btn')) {
      var button = event.target;
      var row = button.closest('.row');
      var commentsRow = row.nextElementSibling;
      commentsRow.classList.toggle('hidden');
      commentsRow.classList.toggle('visible');

      // Add the roll-down animation class when comments become visible
      if (commentsRow.classList.contains('visible')) {
        commentsRow.style.height = 'auto'; // Set height to auto to ensure content is fully visible
        commentsRow.classList.add('roll-down-animation');
      } else {
        commentsRow.style.height = ''; // Reset height to allow transition to take effect
        commentsRow.addEventListener('transitionend', function() {
          commentsRow.classList.remove('roll-down-animation');
        }, { once: true });
      }
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

# data models and database managment systems
Makaranka Aliona, group 153502
Topic: cinema network

<h3>Functional requirements</h3>
<ul>
  <li>User authorisation</li>
  <li>User managment</li>
  <li>Role system (user, admin)</li>
  <li>Logging user actions</li>
  <li>Movies managment</li>
  <li>Sessions managment</li>
  <li>Halls managment</li>
  <li>Cinemas managment</li>
  <li>Sessions managment</li>
  <li>For user: buying tickets</li>
  <li>For user: checking user's tickets</li>
  <li>For user: leaving feedbacks</li>
</ul>
<h3>Entities</h3>
1. user: 
    <pre>
    - user_id - BIGINT PRIMARY KEY NOT NULL
    - login - VARCHAR(255) NOT NULL
    - password - VARCHAR(255) NOT NULL
    - role_id - BIGINT NOT NULL -> role
    </pre>
2. movie
    <pre>
    - movie_id - BIGINT PRIMARY KEY NOT NULL
    - title - VARCHAR(255) NOT NULL
    - description - TEXT NOT NULL
    - rate - INT NOT NULL
    - country - VARCHAR(255) NOT NULL
    - year - INT NOT NULL
    - duration - INTERVAL NOT NULL
    </pre>
3. genre
    <pre>
    - genre_id - BIGINT PRIMARY KEY NOT NULL
    - name - VARCHAR(255) NOT NULL
    </pre>
4. session
    <pre>
    - session_id - BIGINT PRIMARY KEY NOT NULL
    - hall_id - BIGINT NOT NULL -> hall
    - movie_id - BIGINT NOT NULL -> movie
    - time - DATE NOT NULL
    </pre>
5. hall
    <pre>
    - hall_id - BIGINT PRIMARY KEY NOT NULL
    - name - VARCHAR(255) NOT NULL
    - seats_amount - INT NOT NULL
    - cinema_id - BIGINT NOT NULL -> cinema
    </pre>
6. cinema
    <pre>
    - cinema_id - BIGINT PRIMARY KEY NOT NULL
    - name - VARCHAR(255) NOT NULL
    - address - VARCHAR(255) NOT NULL
    </pre>
7. seat
    <pre>
    - seat_id - BIGINT PRIMARY KEY NOT NULL
    - seat_number - INT NOT NULL
    - row - INT NOT NULL
    - hall_id - BIGINT NOT NULL -> hall
    </pre>
8. ticket
    <pre>
    - ticket_id - BIGINT PRIMARY KEY NOT NULL
    - seat_id - BIGINT NOT NULL -> seat
    - session_id - BIGINT NOT NULL -> session
    - user_id - BIGINT NOT NULL -> user
    - date_of_purchase - DATE NOT NULL
    </pre>
9. role
    <pre>
    - role_id - BIGINT PRIMARY KEY NOT NULL
    - name - VARCHAR(255) NOT NULL
    </pre>
10. feedback
    <pre>
    - feedback_id - BIGINT PRIMARY KEY NOT NULL
    - text - TEXT 
    - rate - INT NOT NULL
    - movie_id - BIGINT NOT NULL -> movie
    - user_id - BIGINT NOT NULL -> user
    </pre>
11. log
    <pre>
    - log_id - BIGINT PRIMARY KEY NOT NULL
    - user_id - BIGINT NOT NULL -> user
    - date - DATE NOT NULL
    - activity - VARCHAR(255) NOT NULL
    </pre>
12. movie_genre
    <pre>
    - movie_id - BIGINT NOT NULL -> movie
    - genre_id - BIGINT NOT NULL -> genre
    </pre>

![drawSQL-cinema-export-2023-09-19 (1)](https://github.com/chamomil/dmdbms/assets/93862563/740de227-ead8-4465-8420-374a2bd820bc)


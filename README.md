//DBML to define database structure

Table users {

 id SERIAL [primary key] // id único do usuário gerado automaticamente

 username VARCHAR(50) [not null, unique] // nome do usuário (único)

 created_at TIMESTAMP [default: `CURRENT_TIMESTAMP`] // data de

criação do usuário (automática)

}

Table posts {

 id SERIAL [primary key] // id único do post gerado automaticamente

 user_id INT [not null, ref: > users.id] // id do usuário que criou o

post (chave estrangeira)

 content TEXT [not null] // conteúdo do post (obrigatório)

 image_url VARCHAR(255) // link da imagem (opcional)

 created_at TIMESTAMP [default: `CURRENT_TIMESTAMP`] // data de

criação do post (automática)

 updated_at TIMESTAMP [default: `CURRENT_TIMESTAMP`] // data de

atualização do post (automática)

 likes INT [default: 0] // contador de curtidas (iniciado em 0)

}

//SQL Queries

GRANT ALL PRIVILEGES ON TABLE users TO PUBLIC;

INSERT INTO users (username) VALUES ('john_doe');

SELECT * FROM users;

UPDATE users SET username = 'john_updated' WHERE id = 1;

DELETE FROM users WHERE id = 1;

SELECT * FROM users WHERE id = 1;

INSERT INTO posts (user_id, content, image_url)

VALUES (1, 'Meu primeiro post!', 'https://example.com/image.jpg');

SELECT * FROM posts;

UPDATE posts SET content = 'Conteúdo atualizado!', updated_at =

CURRENT_TIMESTAMP WHERE id = 1;
DELETE FROM posts WHERE id = 1;

SELECT * FROM posts WHERE user_id = 1;

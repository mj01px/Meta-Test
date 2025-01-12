# Documentação do Projeto React

Este documento explica o funcionamento de cada arquivo do projeto, com análise detalhada e um resumo para facilitar o entendimento.

---

## **index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"> <!-- Define o conjunto de caracteres como UTF-8, para suportar vários idiomas. -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- Torna a página responsiva. -->
  <title>Meta Test</title> <!-- Título exibido na aba do navegador. -->
</head>
<body>
  <div id="root"></div> <!-- Contêiner onde o React vai renderizar a aplicação. -->
</body>
</html>
```

### **Resumo:**

- Estrutura básica de um documento HTML5.
- O `div#root` é onde o React irá renderizar toda a aplicação.

---

## **App.js**

```javascript
import Post from "./Post.js"; // Importa o componente Post.

export default function App() {
  return <div><Post /></div>; // Retorna o componente Post dentro de uma div.
}
```

### **Resumo:**

- `App.js` é o componente principal da aplicação.
- Ele carrega o componente `Post`, que contém o conteúdo principal da interface.

---

## **FollowButton.js**

```javascript
import { useState } from "react"; // Importa o hook useState.

export default function FollowButton() {
    const [following, setFollowing] = useState(false); // Estado para controlar se está seguindo.
    return (
        <div
            id="follow-button"
            className={following ? "following" : "not-following"} // Altera a classe dinamicamente.
            onClick={() => setFollowing(!following)} // Alterna o estado quando clicado.
        >
            {following == true ? "Following" : "Follow"}
        </div> // Mostra texto de acordo com o estado.
    );
}
```

### **Resumo:**

- Botão que alterna entre "Follow" e "Following" com base no estado.
- Usa o `useState` para gerenciar o estado de "seguindo".

---

## **index.js**

```javascript
import React, { StrictMode } from "react"; // Importa React e StrictMode.
import { createRoot } from "react-dom/client"; // Nova API para renderizar componentes.
import "./index.css"; // Estilos globais.

import App from "./App"; // Importa o componente principal.

const root = createRoot(document.getElementById("root")); // Encontra o elemento root no HTML.
root.render(
    <StrictMode>
        <App /> {/* Renderiza o componente App dentro de StrictMode. */}
    </StrictMode>
);
```

### **Resumo:**

- O ponto de entrada da aplicação React.
- Usa `createRoot` para renderizar o componente `App` no DOM.

---

## **LikeButton.js**

```javascript
import { useState } from "react"; // Importa o hook useState.

const emptyHeartImage = "https://i.imgur.com/wIq3Wbq.png"; // Imagem do coração vazio.
const fullHeartImage = "https://i.imgur.com/vyX9Vnx.png"; // Imagem do coração cheio.

export default function LikeButton() {
    const [likes, setLikes] = useState(0); // Estado para contar os likes.

    return (
        <div className="like-info">
            <div className="like-button" onClick={() => setLikes(likes + 1)}> {/* Incrementa likes no clique. */}
                {likes > 0 ? (
                    <img src={fullHeartImage} alt="Heart for like button" /> // Exibe coração cheio.
                ) : (
                    <img src={emptyHeartImage} alt="Empty heart for like button" /> // Exibe coração vazio.
                )}
            </div>
            <p>{likes == 1 ? `  ${likes} Like` : `${likes} Likes`}</p> {/* Pluraliza dinamicamente. */}
        </div>
    );
}
```

### **Resumo:**

- Botão de curtida com contagem de likes.
- Exibe diferentes imagens com base no número de curtidas.

---

## **Post.js**

```javascript
import FollowButton from "./FollowButton.js"; // Botão de seguir.
import LikeButton from "./LikeButton.js"; // Botão de curtida.

const postImage = "https://i.imgur.com/ZUZiJ4y.png"; // Imagem do post.
const userImage = "https://i.imgur.com/lfoiQZs.png"; // Imagem do perfil.

export default function Post() {
    return (
        <div className="post">
            <div className="user-info">
                <img id="profile-img" src={userImage} alt="Profile Image" /> {/* Foto do perfil. */}
                <p>Hipthehippocorn</p> {/* Nome do usuário. */}
                <FollowButton /> {/* Componente de botão seguir. */}
            </div>
            <img id="post-img" src={postImage} alt="Post Image" /> {/* Imagem principal do post. */}
            <LikeButton /> {/* Componente de botão curtir. */}
        </div>
    );
}
```

### **Resumo:**

- Componente que monta um post com:
    - Foto de perfil.
    - Nome do usuário.
    - Botões de seguir e curtir.
    - Imagem do post.

---

### **Considerações Finais:**

- O projeto utiliza React com hooks (`useState`) para gerenciar estados.
- Os componentes estão bem organizados e reusáveis, o que é uma boa prática.
- A estrutura facilita a manutenção e a adicião de novas funcionalidades.


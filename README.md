# Landing page da Casa Contente

Página provisória que fica no ar enquanto o site novo não fica pronto. É um único arquivo, o `index.html`. Ele não tem build nem dependências: basta publicar o arquivo.

## Último post do Instagram

A seção do Instagram mostra o post mais recente do [@casacontente](https://www.instagram.com/casacontente/). Como a página não tem servidor próprio, quem lê o perfil é o [Behold](https://behold.so). Ele transforma os posts num feed JSON público, e a página busca esse feed.

Enquanto o feed não estiver configurado, ou se o Behold estiver fora do ar, a seção mostra apenas um convite para seguir o perfil. A página continua funcionando normalmente.

### Como conectar

1. **Confira o tipo de conta do Instagram.** O perfil precisa ser profissional, do tipo comercial ou criador de conteúdo. Para conferir, abra o app e vá em *Configurações → Tipo de conta e ferramentas*.
2. **Crie uma conta no Behold** em [behold.so](https://behold.so). O plano gratuito é suficiente.
3. **Conecte o Instagram.** No painel do Behold, adicione uma conta do Instagram e entre com o login do @casacontente.
4. **Crie um feed do tipo JSON.** Ao criar o feed, escolha a opção JSON, e não a de widget. O Behold vai mostrar uma URL parecida com esta:

   ```
   https://feeds.behold.so/AbCdEf123456
   ```

5. **Cole a URL no `index.html`.** Procure esta linha no `<script>` do final do arquivo:

   ```js
   var FEED_INSTAGRAM = "";
   ```

   e coloque a URL do feed entre as aspas:

   ```js
   var FEED_INSTAGRAM = "https://feeds.behold.so/AbCdEf123456";
   ```

6. **Publique e confira.** Abra a página. O card deve mostrar a foto, a legenda e a data do último post, e o título deve mudar para "Último post no Instagram".

### Bom saber

- **Atualização:** no plano gratuito, o feed do Behold não atualiza na hora. Um post novo pode levar algumas horas para aparecer. Os planos pagos atualizam com mais frequência.
- **Vídeos e reels** aparecem com a imagem de capa e um ícone de play.
- **Legenda:** as hashtags do final da legenda são removidas, e textos longos são cortados depois de algumas linhas.
- **Se o post não aparecer:** abra a URL do feed direto no navegador. Se ela não devolver um JSON com os posts, o problema está na conexão com o Behold, e não na página. Nesse caso, reconecte a conta do Instagram no painel do Behold.
- **Testar localmente:** se o post não aparecer com o arquivo aberto direto do disco (`file://`), alguns navegadores podem estar bloqueando a busca do feed. Nesse caso, rode um servidor simples na pasta, por exemplo com `python3 -m http.server`, e acesse `http://localhost:8000`.

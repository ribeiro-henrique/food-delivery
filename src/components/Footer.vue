<template>
  <footer id="footer">
    <p>Açaí Delivery &copy; 2023</p>
    <a href="https://github.com/ribeiro-henrique" target="_blank" rel="noopener noreferrer">Github</a> |
    <a href="https://www.linkedin.com/in/hesr/" target="_blank" rel="noopener noreferrer">Linkedin</a>
  </footer>
</template>

<script>
  export default {
    name: "Footer"
  }

</script>

<style scoped>

  #footer {
    height: 200px;
    background-color: #371B34;
    border-top: 4px solid #fff;
    color: #fcba03;
    display: flex;
    align-items: center;
    justify-content: center;
    bottom: 0;
    width: 100%;
    gap: 10px;
  }

  #footer p {
    color: #fff;
  }
  
  #footer a {
    text-decoration: none;
    color: #fcba03;
    font-weight: 700;
    transition: .5s;
  }

  #footer a:hover {
    color: #fff;
  }
</style>
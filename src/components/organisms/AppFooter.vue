<script setup lang="ts"></script>

<template>
  <footer>
    <ul class="footer-list">
      <li>
        <p>Follow us on social media</p>

        <div class="social-btns">
          <a href="https://instagram.com" target="_blank" aria-label="Our instagram">
            <img src="/src/assets/insta-logo.svg" alt="instagram" />
          </a>

          <a href="https://facebook.com" target="_blank" aria-label="Our facebok">
            <img src="/src/assets/facebook-logo.svg" alt="facebook" />
          </a>

          <a href="https://tiktok.com" target="_blank" aria-label="Our tiktok">
            <img src="/src/assets/tiktok-log.svg" alt="tiktok" />
          </a>
        </div>
      </li>
      <li>
        <p>Le Forel</p>
        <p>Veerweg 36</p>
        <p>4493 AS Kamperland</p>
      </li>
      <li>
        <p>Telefoonnummer: <span class="text-light">+31 58 648 4862</span></p>
        <p>Email: <span class="text-light">info@leforel.nl</span></p>
        <p>Openingstijden: <span class="text-light">MA - ZO 18:00</span></p>
      </li>
    </ul>
  </footer>
</template>

<style lang="css" scoped>
footer {
}

.footer-list {
  display: flex;
  flex-flow: row;
  justify-content: space-around;
  align-items: center;
  list-style-type: none;
  text-transform: uppercase;
  background-color: var(--footer-bg);
  color: var(--text-color-light);
  margin: 0;
  padding: 3rem 0;

  .social-btns {
    display: flex;
    flex-flow: row;
    gap: 0.5rem;
    margin-top: 1rem;

    & a {
      display: flex;
      flex-flow: column;
      padding: 0.5rem;
      background-color: var(--btn-color);
      border-radius: 50px;

      img {
        width: 1.5rem;
      }

      &:hover {
        transform: scale(1.1);
      }
    }
  }

  li {
    display: flex;
    flex-flow: column;
    justify-content: space-between;
    gap: 0.3rem;

    .text-light {
      font-weight: 300;
      margin-left: 0.5rem;
    }
  }
}

@media (max-width: 50rem) {
  .footer-list {
    flex-flow: column;
    justify-content: space-between;
    align-items: center;
    gap: 2.5rem;

    .social-btns {
      align-items: center;
      justify-content: center;
    }

    li {
      text-align: center;
    }
  }
}
</style>

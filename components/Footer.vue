<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <h2 class="footer-title">Contact Us</h2>

        <div class="footer-grid">
          <div class="glass-bg form-container">
            <form class="contact-form" @submit.prevent="sendEmail">
              <input v-model="form.name" type="text" placeholder="Name" class="input-field">
              <input v-model="form.email" type="email" placeholder="Email" class="input-field">
              <textarea v-model="form.message" placeholder="Message" rows="3" class="input-field"></textarea>
              <button type="submit" class="btn-submit">Send Message</button>
            </form>
          </div>

          <div class="info-container">
            <div class="glass-bg contact-info">
              <h3 class="info-title">Contact Info</h3>
              <ul class="info-list">
                <li v-for="item in contactInfo" :key="item.title" class="info-item">
                  <Icon :icon="item.icon" class="info-icon" />
                  <span class="info-text">{{ item.address }}</span>
                </li>
              </ul>
            </div>

            <div class="glass-bg social-media">
              <h3 class="info-title">Connect With Us</h3>
              <div class="social-icons">
                <a v-for="social in socialMedia" :key="social.name" :href="social.link" class="social-link">
                  <Icon :icon="social.icon" class="social-icon" />
                </a>
              </div>
            </div>
          </div>
        </div>

        <div class="footer-bottom">
          <p>&copy; {{ new Date().getFullYear() }} SchieldCentre. All rights reserved.</p>
          <p>Powered by <a href="https://ghub.org" class="ghub-link">ghub.org</a></p>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { ref } from 'vue'
import { Icon } from '@iconify/vue'

const contactInfo = ref([
  { title: 'Phone', icon: 'heroicons:phone', address: '+254110883547' },
  { title: 'E-mail', icon: 'heroicons:envelope', address: 'schieldcenter@gmail.com' },
  { title: 'Address', icon: 'heroicons:map-pin', address: 'Noosolian Namannga-Highway' },
])

const socialMedia = ref([
  { name: 'Facebook', icon: 'entypo-social:facebook', link: '#' },
  { name: 'Twitter', icon: 'entypo-social:twitter', link: '#' },
  { name: 'Instagram', icon: 'entypo-social:instagram', link: '#' },
  { name: 'LinkedIn', icon: 'entypo-social:linkedin', link: '#' },
  { name: 'YouTube', icon: 'entypo-social:youtube', link: '#' },
])

const form = ref({ name: '', email: '', message: '' })

const sendEmail = () => {
  const mailtoLink = `mailto:schieldcentreaaaaaaaaaa@gmail.com?subject=Contact Form Submission&body=Name: ${form.value.name}%0D%0AEmail: ${form.value.email}%0D%0AMessage: ${form.value.message}`
  window.location.href = mailtoLink
}
</script>

<style scoped>
.footer {
  background: linear-gradient(to top, #1e1b4b, #312e81, #581c87);
  color: white;
  padding: 2rem 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.footer-content {
  background-color: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 1rem;
  padding: 1.5rem;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

.footer-title {
  font-size: 1.875rem;
  font-weight: bold;
  text-align: center;
  margin-bottom: 1.5rem;
}

.footer-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
}

@media (min-width: 768px) {
  .footer-grid {
    grid-template-columns: 1fr 1fr;
  }
}

.glass-bg {
  background-color: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 0.5rem;
  padding: 1rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.input-field {
  width: 100%;
  padding: 0.5rem 0.75rem;
  border-radius: 0.375rem;
  background-color: rgba(255, 255, 255, 0.2);
  color: white;
  border: none;
}

.input-field:focus {
  outline: none;
  box-shadow: 0 0 0 2px rgba(253, 224, 71, 0.5);
}

.btn-submit {
  width: 100%;
  background-color: #fde047;
  color: #312e81;
  font-weight: 600;
  padding: 0.5rem 1rem;
  border-radius: 0.375rem;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s;
}

.btn-submit:hover {
  background-color: #fcd34d;
}

.info-container {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.info-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.info-list {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.info-item {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
}

.info-icon {
  width: 1.25rem;
  height: 1.25rem;
  color: #fde047;
  margin-right: 0.5rem;
}

.info-text {
  font-size: 0.875rem;
}

.social-icons {
  display: flex;
  gap: 0.75rem;
}

.social-link {
  color: white;
  transition: color 0.3s;
}

.social-link:hover {
  color: #fde047;
}

.social-icon {
  width: 1.5rem;
  height: 1.5rem;
}

.footer-bottom {
  text-align: center;
  margin-top: 1.5rem;
  font-size: 0.875rem;
  color: #d1d5db;
}

.ghub-link {
  color: #fde047;
  text-decoration: none;
}

.ghub-link:hover {
  text-decoration: underline;
}
</style>
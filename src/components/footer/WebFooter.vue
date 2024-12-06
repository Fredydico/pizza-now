<template>
  <footer>
    <div class="container py-5 border-top border-bottom">
      <div class="footer-flex">
        <div class="footer-col">
          <a href="/" class="d-flex mb-5">
            <img src="../../assets/logo-alt.svg" class="img-fluid" alt="Foodnow Logo" />
          </a>
          <h4 class="paySum">Find Us :</h4>
          <div class="social-icons">
            <a href="#" class="btn-social">
              <img src="../../assets/image/facebook.svg" class="contact-icon" alt="" />
            </a>
            <a href="#" class="btn-social">
              <img src="../../assets/image/instagram.svg" class="contact-icon" alt="" />
            </a>
            <a href="#" class="btn-social">
              <img src="../../assets/image/youtube.svg" class="contact-icon" alt="" />
            </a>
          </div>
        </div>
        <div class="footer-col">
          <h4 class="paySum">Navigation</h4>
          <ul class="nav-links d-flex justify-content-between w-50 fs-5">
            <div>
              <li><a href="#" class="nav-link">Home</a></li>
              <li><a href="#" class="nav-link">Order</a></li>
              <li><a href="#" class="nav-link">About</a></li>
              <li><a href="#" class="nav-link">Blog</a></li>
            </div>
            <div>
              <li><a href="#" class="nav-link">Contact</a></li>
              <li><a href="#" class="nav-link">Login</a></li>
              <li><a href="#" class="nav-link">Register</a></li>
            </div>
          </ul>
        </div>
        <div class="footer-col">
          <h4 class="paySum">Contact</h4>
          <ul class="contact-list fs-5">
            <li>
              <img src="../../assets/image/mail.svg" class="contact-icon" alt="" />
              Food.now@mail.com
            </li>
            <li>
              <img src="../../assets/image/phone.svg" class="contact-icon" alt="" />
              +62848477102943
            </li>
            <li>
              <img src="../../assets/image/whatsapp.svg" class="contact-icon" alt="" />
              +628184938494
            </li>
          </ul>
        </div>
        <div class="footer-col">
          <h4 class="paySum">Location</h4>
          <ul class="location">
            <li>
              <img src="../../assets/image/location.svg" class="contact-icon" alt="" />
              <div>
                <h5>Kerobokan</h5>
                <p>Jl. Raya Kerobokan Br Taman, Kuta No.98, Kerobokan Kelod, Kec. Kuta Utara, Kabupaten Badung, Bali 80361</p>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="container py-3">
      <p class="copyright">Copyright © 2022 Foodnow. All Rights Reserved. Powered by PT. Timedoor Indonesia. | Privacy Policy This site is protected by reCAPTCHA and the Google Privacy Policy and Terms of Service apply.</p>
    </div>
  </footer>
</template>

<style>
.contact-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.contact-list li {
  float: left;
  margin-right: 20px;
  margin-bottom: 0.875rem;
}

.contact {
  display: flex;
  align-items: center;
}

.btn-social {
  border: #e77e23 1px solid;
}

.btn-social:hover {
  background-color: rgba(231, 125, 35, 0.3);
}

.footer-flex {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.footer-col {
  flex: 1;
  min-width: 200px;
  margin-right: 20px;
}

.footer-col:last-child {
  margin-right: 0;
}

.copyright {
  text-align: center;
  max-width: 48.5rem;
  margin: auto;
  font-size: 13px;
}

.btn-social {
  width: 2.5rem;
  height: 2.5rem;
  padding: 0;
  border-radius: 50%;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  margin-right: 1rem;
}

.btn-social img {
  margin: 0;
}

.contact-icon {
  height: 1.25rem;
  width: 1.25rem;
  object-fit: contain;
  margin-right: 0.5rem;
}

footer {
  font-size: 1.125rem;
}

footer h4 {
  margin-bottom: 1.25rem;
}

.nav-links {
  list-style: none;
  padding: 0;
}

.nav-links li {
  margin-bottom: 0.875rem;
}

footer ul {
  list-style: none;
  padding: 0;
}

footer ul li {
  display: flex;
  align-items: center;
  margin-bottom: 0.875rem;
}

.location li {
  align-items: flex-start;
}

@media (max-width: 768px) {
}
</style>

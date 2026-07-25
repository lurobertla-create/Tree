// =========================================================
// Milton Keynes Tree Surgeons — site scripts
// Mobile nav, quote form handling, FAQ accordion, scroll reveal
// =========================================================

document.addEventListener('DOMContentLoaded', function () {

  /* ---------- Footer year ---------- */
  var yearEl = document.getElementById('year');
  if (yearEl) yearEl.textContent = new Date().getFullYear();

  /* ---------- Mobile nav toggle ---------- */
  var menuToggle = document.getElementById('menuToggle');
  var mainNav = document.getElementById('mainNav');

  if (menuToggle && mainNav) {
    menuToggle.addEventListener('click', function () {
      var isOpen = mainNav.classList.toggle('is-open');
      menuToggle.setAttribute('aria-expanded', isOpen ? 'true' : 'false');
    });

    // Close menu when a link is tapped
    mainNav.querySelectorAll('a').forEach(function (link) {
      link.addEventListener('click', function () {
        mainNav.classList.remove('is-open');
        menuToggle.setAttribute('aria-expanded', 'false');
      });
    });
  }

  /* ---------- FAQ accordion ---------- */
  var faqButtons = document.querySelectorAll('.faq-question');
  faqButtons.forEach(function (btn) {
    var answer = btn.nextElementSibling;
    btn.addEventListener('click', function () {
      var isOpen = btn.getAttribute('aria-expanded') === 'true';

      // Close all other items
      faqButtons.forEach(function (otherBtn) {
        if (otherBtn !== btn) {
          otherBtn.setAttribute('aria-expanded', 'false');
          otherBtn.nextElementSibling.style.maxHeight = null;
        }
      });

      // Toggle current item
      btn.setAttribute('aria-expanded', isOpen ? 'false' : 'true');
      answer.style.maxHeight = isOpen ? null : answer.scrollHeight + 'px';
    });
  });

  /* ---------- Photo upload label update (visual only) ---------- */
  var photoInput = document.getElementById('photo');
  var photoLabelText = document.getElementById('photoLabelText');
  if (photoInput && photoLabelText) {
    photoInput.addEventListener('change', function () {
      if (photoInput.files && photoInput.files.length > 0) {
        photoLabelText.textContent = photoInput.files[0].name;
      } else {
        photoLabelText.textContent = 'Upload a photo of the tree (optional)';
      }
    });
  }

  /* ---------- Quote form handling (no backend — front-end only) ---------- */
  var quoteForm = document.getElementById('quoteForm');
  var formSuccess = document.getElementById('formSuccess');

  if (quoteForm) {
    quoteForm.addEventListener('submit', function (e) {
      e.preventDefault();

      if (!quoteForm.checkValidity()) {
        quoteForm.reportValidity();
        return;
      }

      // Simulate a successful lead submission.
      // Replace this block with a real form handler (e.g. Formspree, Netlify Forms,
      // or a backend endpoint) when ready to receive live enquiries.
      var submitBtn = quoteForm.querySelector('button[type="submit"]');
      var originalText = submitBtn.textContent;
      submitBtn.disabled = true;
      submitBtn.textContent = 'Sending...';

      setTimeout(function () {
        quoteForm.reset();
        photoLabelText && (photoLabelText.textContent = 'Upload a photo of the tree (optional)');
        submitBtn.disabled = false;
        submitBtn.textContent = originalText;

        if (formSuccess) {
          formSuccess.hidden = false;
          formSuccess.scrollIntoView({ behavior: 'smooth', block: 'center' });
        }
      }, 500);
    });
  }

  /* ---------- Sticky header shadow on scroll ---------- */
  var header = document.getElementById('siteHeader');
  if (header) {
    var onScroll = function () {
      if (window.scrollY > 8) {
        header.style.boxShadow = '0 8px 24px -16px rgba(0,0,0,0.4)';
      } else {
        header.style.boxShadow = 'none';
      }
    };
    window.addEventListener('scroll', onScroll, { passive: true });
    onScroll();
  }

  /* ---------- Scroll reveal animations ---------- */
  var revealEls = document.querySelectorAll('.reveal');
  var prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  if (prefersReducedMotion || !('IntersectionObserver' in window)) {
    revealEls.forEach(function (el) { el.classList.add('is-visible'); });
  } else {
    var observer = new IntersectionObserver(function (entries) {
      entries.forEach(function (entry) {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible');
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });

    revealEls.forEach(function (el) { observer.observe(el); });
  }

});

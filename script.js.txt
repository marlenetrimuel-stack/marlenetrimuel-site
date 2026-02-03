// Mobile nav toggle
const toggle = document.querySelector(".nav-toggle");
const mobileNav = document.querySelector("#mobileNav");

if (toggle && mobileNav) {
  toggle.addEventListener("click", () => {
    const isOpen = mobileNav.classList.toggle("show");
    toggle.setAttribute("aria-expanded", String(isOpen));
  });

  // Close mobile menu on link click
  mobileNav.querySelectorAll("a").forEach((a) => {
    a.addEventListener("click", () => {
      mobileNav.classList.remove("show");
      toggle.setAttribute("aria-expanded", "false");
    });
  });
}

// CTA placeholders safety
// If you deploy without Calendly link, prevent broken navigation.
const calendlyPlaceholders = ["#btnBookTop", "#btnBookMobile", "#btnBookHero", "#btnBookContact"];
calendlyPlaceholders.forEach((sel) => {
  const el = document.querySelector(sel);
  if (!el) return;
  if (el.getAttribute("href") === "CALENDLY_LINK_HERE") {
    el.addEventListener("click", (e) => {
      e.preventDefault();
      alert("Booking link will be added shortly. For now, please use the inquiry form below.");
      document.querySelector("#contact")?.scrollIntoView({ behavior: "smooth" });
    });
  }
});

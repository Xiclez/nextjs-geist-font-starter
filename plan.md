```markdown
# Detailed Implementation Plan

## 1. File Structure and New Components
- **New Directory**: Create a folder at `src/components/landing` to house all landing page–specific components.
- **New Component Files**:
  - `HeroSection.tsx`
  - `ServiceOverview.tsx`
  - `CaseStudies.tsx`
  - `WhyChooseUs.tsx`
  - `LeadCaptureForm.tsx`
  - `TrustBuilders.tsx`
  - `BlogSection.tsx` (optional)
  - `Footer.tsx`
- **Main Landing Page**: Create or update the main page file at `src/app/page.tsx` to compose and render these components.

---

## 2. File-by-File Changes

### 2.1. File: `src/app/page.tsx`
- **Purpose**: Serves as the primary landing page.
- **Changes**:
  - Import the Next.js `Head` component and add SEO meta tags (title, description, viewport).
  - Import all landing-specific components (HeroSection, ServiceOverview, etc.).
  - Compose page sections in the following order:
    1. Header (if needed)
    2. Hero Section with catchy headline and CTAs
    3. Service Overview section for the 8 categories
    4. Case Studies / Portfolio section
    5. Why Choose Us section (value proposition)
    6. Lead Capture Form (with validation and error messages)
    7. Trust Builders (testimonials and certifications)
    8. Blog / Resources section (optional)
    9. CTA Footer with contact info and social links
  - Wrap the main content with an error boundary component if desired for enhanced error handling.

---

### 2.2. File: `src/components/landing/HeroSection.tsx`
- **Purpose**: Creates the above–the–fold section.
- **Implementation**:
  - Display the headline: “Secure. Scalable. Smarter Software & Marketing.”
  - Add a short subheading explaining the services.
  - Render CTA buttons “Get a Free Consultation” and “Book a Demo”.
  - Use a background image with an `<img>` tag:
    ```jsx
    <img
      src="https://placehold.co/1920x1080?text=Digital+Transformation+Fusion+Graphic"
      alt="Detailed digital transformation fusion graphic showcasing technology and marketing integration in a sleek, modern style"
      onError={(e) => { e.currentTarget.style.display = 'none'; }}
    />
    ```
  - Ensure the section is responsive with modern typography and spacing applied via CSS (or CSS modules).

---

### 2.3. File: `src/components/landing/ServiceOverview.tsx`
- **Purpose**: Summarizes the eight service categories.
- **Implementation**:
  - Use an array of service objects for:
    - Custom Software Development
    - Cloud & Virtualization Solutions
    - Cybersecurity & Ethical Testing
    - Automation & Process Optimization
    - Data & Analytics
    - Consulting & IT Advisory
    - Training & Support
    - Marketing & Growth Services
  - For each service, render a card using the existing UI card component (`src/components/ui/card.tsx`).
  - Instead of external icons, use stylized text or CSS shapes to represent icons.
  - Add a “Learn More” link to each card.

---

### 2.4. File: `src/components/landing/CaseStudies.tsx`
- **Purpose**: Display real/demo projects to build credibility.
- **Implementation**:
  - Layout a grid or list of case study cards, each containing:
    - A small placeholder image using:
      ```jsx
      <img
        src="https://placehold.co/800x600?text=Case+Study+Screenshot"
        alt="Placeholder image for case study screenshot displaying problem-solution-result flow"
        onError={(e) => { e.currentTarget.style.display = 'none'; }}
      />
      ```
    - A brief write-up with sections for problem, solution, and results.
  - Use error handling for image loading and ensure consistency in layout using existing UI components.

---

### 2.5. File: `src/components/landing/WhyChooseUs.tsx`
- **Purpose**: Present the value proposition.
- **Implementation**:
  - Render a bulleted list with highlights such as:
    - "Full-spectrum: from software to marketing."
    - "Cybersecurity-first approach."
    - "Tailored solutions for SMEs."
  - Use custom CSS for modern bullet styling and spacing.

---

### 2.6. File: `src/components/landing/LeadCaptureForm.tsx`
- **Purpose**: Capture visitor details for consultations and demos.
- **Implementation**:
  - Build a form with fields: Name, Email, Company, and Message.
  - Integrate client-side input validation with friendly error messages.
  - Use existing UI form components (e.g., input, label, button) in `src/components/ui/`.
  - Add CTA buttons (e.g., “Submit”, “Book a Demo”) and integrate external booking links (Calendly/Google Meet) as needed.
  - Handle errors gracefully and show user feedback on submission issues.

---

### 2.7. File: `src/components/landing/TrustBuilders.tsx`
- **Purpose**: Build trust with testimonials and certifications.
- **Implementation**:
  - Render testimonial cards and certification badges using text labels styled via CSS.
  - Utilize placeholder images where necessary with proper alt texts.
  - Ensure layout remains intact even if images fail to load.

---

### 2.8. File: `src/components/landing/BlogSection.tsx` (Optional)
- **Purpose**: Showcase thought leadership through technology and marketing insights.
- **Implementation**:
  - Display a card layout for recent blog posts, each with title, excerpt, and a “Read More” link.
  - Use modern typography and spacing without external image services (only use placeholder images if a visual is essential).

---

### 2.9. File: `src/components/landing/Footer.tsx`
- **Purpose**: Provide a final call-to-action and quick contact details.
- **Implementation**:
  - Reiterate CTAs (“Ready to transform your business? Contact us today.”).
  - List social media text links (LinkedIn, X, Instagram, YouTube) and basic contact info.
  - Use semantic HTML elements for accessibility and SEO considerations.

---

### 2.10. File: `src/app/globals.css`
- **Purpose**: Apply global styling changes.
- **Changes**:
  - Define brand color variables, typography, and spacing rules for a modern, clean aesthetic.
  - Add responsive design breakpoints ensuring mobile-first layout.
  - Include CSS classes for sections (e.g., hero-bg, grid layouts for cards, form styling) to be referenced across landing components.
  - Ensure fallback styles are in place for any image or component error.

---

## 3. Integration & UX Considerations
- **Error Handling**: All form inputs include inline validation; images use `onError` handlers to maintain design integrity.
- **Performance**: Optimize images with defined dimensions and responsive CSS, and include meta tags for swift page load and SEO readiness.
- **UI/UX**: Use clean typography, ample whitespace, and clear call-to-action elements to create a modern, sleek interface without dependency on external icon libraries.
- **Optional Enhancements**: Future integration of a live chat or chatbot (LLM-based using OpenRouter with default model `anthropic/claude-sonnet-4`) for FAQs and lead capture may be added after initial launch.

---

## Summary
- Created a landing page in `src/app/page.tsx` with modular components in `src/components/landing`.
- Built sections for hero, services, case studies, value proposition, lead capture, trust builders, blog (optional), and footer.
- Updated global CSS in `src/app/globals.css` for modern, responsive design.
- Implemented error handling in forms and fallback for images.
- Reused existing UI components for consistency.
- The design uses modern typography, color, and layout without external icon libraries.
- Future enhancements include live chat integration using an LLM-based approach.

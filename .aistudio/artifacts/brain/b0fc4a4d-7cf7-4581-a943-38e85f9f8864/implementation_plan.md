# Implementation Plan — SSH.JC Brand Identity & Sleek Glass Design System

## 1. Design Brief & Direction
- **Logo Concept**: **Cybernetic Keyhole** — A precision-crafted geometric vector integrating an OpenSSH cryptographic key bit within a concentric tunneling data conduit.
- **Aesthetic**: **Sleek Modern Glass** — Deep backdrop blurs (`backdrop-blur-xl`), hairline structural dividers (`1px solid #273647`), subtle ambient glow states, and crisp technical typography.
- **Dropdown / Select Experience**: Custom popover with live search filter, keyboard accessibility (Arrow keys, Enter, Esc), animated caret rotation, and option checkmarks.
- **Micro-Interactions**: Tactile button presses (`scale: 0.98`), SVG animated check drawing, and smooth spring popovers.

---

## 2. Proposed Architecture & New Modules

### A. Brand Logo System (`src/components/ui/Logo.tsx`)
- **Vector Construction**: Clean 256×256 SVG geometry:
  - Outer concentric hex-tunnel ring with gradient stroke (`#00e5ff` to `#38bdf8`).
  - Central keyhole silhouette representing protected host access.
  - Symmetrical cryptographic bit paths indicating encrypted tunnel packets.
- **Variants**:
  - `icon`: Compact mark for sidebar, header, and favicon.
  - `full`: Complete lockup with typography (`SSH.JC` + `CONTROL CENTER`).
  - Animated pulse ring for active ingress states.
- **Favicon**: Integrated SVG favicon in `index.html`.

### B. Custom UI Component Suite (`src/components/ui/`)
1. **`Button.tsx`**:
   - Glass surfaces with hairline borders and kinetic focus states.
   - Variants: `primary` (electric cyan with glow), `secondary` (glass slate), `destructive` (crimson hold-to-confirm), `ghost`.
   - Loading spinner state with preserved layout geometry.
2. **`Select.tsx` (Custom Popover with Search Filter)**:
   - Full replacement for native `<select>` elements.
   - Animated chevron caret with 180° rotation.
   - Inline search filter for instant option filtering.
   - Keyboard accessible (`Tab`, `ArrowDown`, `ArrowUp`, `Enter`, `Escape`).
   - Outside click detection and smooth `motion` entrance (`scale: 0.98 → 1`, `opacity: 0 → 1`).
3. **`Checkbox.tsx`**:
   - Custom square glass container with cyan glow on checked state.
   - SVG checkmark path animation drawn via Framer Motion (`pathLength: 0 → 1`).
   - Accessible hidden native input for form compatibility and keyboard toggling (`Space`).
4. **`Badge.tsx`**:
   - Precision hardware status chips with tabular numerals and hairline borders.

### C. Interface Layout & Component Upgrades
- **Sidebar & Header**: Integrates the new Cybernetic Keyhole logo, elevated glass backdrop blur, and refined collapse transitions.
- **Install Wizard**: Upgraded with custom `Select` for providers, custom `Checkbox` for sudo admin and password authentication toggles, and modern glass cards.
- **SSH Bastion**: Upgraded with custom `Select` for `PermitRootLogin` and `PasswordAuthentication` directives.
- **Tunnel Fleet**: Upgraded with custom `Select` for execution modes (nohup vs systemd) and tactile launch/stop buttons.

---

## 3. Preservation & Verification
- Real backend endpoints (`/api/system/status`, `/api/jobs/*`, `/api/ssh/*`, `/api/tunnels/*`) remain fully wired.
- Port 3000 safeguard remains strictly locked.
- All 10 automated test suites (`npm test`) remain green.
- Compilation and linting (`tsc --noEmit`) verified.

---

## 4. Execution Steps
1. Create `src/components/ui/Logo.tsx` with precision SVG geometry and lockup variants.
2. Create custom `Button.tsx`, `Select.tsx`, `Checkbox.tsx`, and `Badge.tsx` components.
3. Update `index.html` with the new SVG favicon and styling.
4. Integrate the new UI components and Logo across `Sidebar.tsx`, `Header.tsx`, `InstallWizard.tsx`, `SshManager.tsx`, and `TunnelManager.tsx`.
5. Verify build, linting, tests, and runtime server responsiveness.

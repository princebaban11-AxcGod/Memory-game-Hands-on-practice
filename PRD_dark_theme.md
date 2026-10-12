# Product Requirements Document: Dark Theme

## Summary

Add an optional dark theme to the Memory Game in `memory-game.html`. Players can switch between the existing light appearance and a dark appearance while playing. The selected theme should persist across reloads in the same browser.

This document defines requirements only; it does not implement the feature.

## Background

The game is a standalone HTML, CSS, and JavaScript application. Its styles are currently embedded in `memory-game.html` and use CSS custom properties for some colors, alongside hard-coded light backgrounds and text colors. Game scores are saved in `localStorage` under `memoryGameScores`.

## Goals

- Provide a clear control to switch between light and dark themes.
- Make every part of the game readable and usable in both themes.
- Remember the player's selected theme without changing saved scores or game behavior.
- Preserve the current light appearance and behavior for players who have not selected a theme.

## Non-goals

- Redesigning the game or changing its rules, scoring, layouts, or card symbols.
- Changing how best scores are calculated, displayed, or stored.
- Adding dependencies, a build process, or a separate stylesheet.
- Automatically selecting a theme from the operating system setting. The initial experience remains the existing light theme unless the player has previously selected a theme.

## User stories

- As a player, I want to switch to a dark theme so I can play in a darker environment.
- As a player, I want the game to remember my theme choice when I return.
- As a player, I want all game content and controls to remain legible and usable in either theme.

## Functional requirements

1. Add a theme toggle to the game interface, visible in both themes and available without starting a game.
2. The toggle switches immediately between light and dark themes without resetting the board, moves, timer, rating, or current game state.
3. On first visit, show the existing light theme.
4. Save the player's theme choice in a dedicated `localStorage` key. Do not reuse or modify `memoryGameScores`.
5. Restore a valid saved theme when the page loads. If no valid preference is saved, use the light theme.
6. Theme switching and preference restoration must not alter score contents or interfere with score saving and display.
7. Apply the selected theme consistently to the page background, text, controls, statistics panel, card backs and faces, best-scores area, focus indicators, and game-complete dialog and backdrop. Keep matched/unmatched card states visually distinguishable.
8. Keep the card symbols and their meaning unchanged in both themes.

## Accessibility and usability requirements

- Implement the toggle as a native button with an accessible name that identifies its action or purpose.
- Expose its current state to assistive technology, for example with `aria-pressed`, and keep that state synchronized with the selected theme.
- The control must work with keyboard activation and retain a visible focus indicator in both themes.
- Maintain readable contrast for text, controls, cards, focus indicators, and modal content in both themes.
- Do not rely on color alone to communicate card matches, the selected grid size, or the toggle state.
- Keep the existing responsive layout and keyboard card controls working.

## Design and implementation guidance

- Reuse and extend the existing CSS custom-property approach so colors can be switched centrally.
- Prefer a theme attribute or class on the document root and define light and dark values for the relevant color properties.
- Replace hard-coded theme-dependent colors where necessary so no section remains unintentionally light in dark mode.
- Keep the current light theme's colors and visual appearance as the baseline.
- Use a separate, namespaced storage key for the theme preference. Do not clear or rewrite other local storage data.
- Keep the game logic independent of theme selection.

## Acceptance criteria

- [ ] A player can switch from light to dark and back using the theme control.
- [ ] Switching themes during an active game preserves the board, card states, moves, timer, and rating.
- [ ] The selected theme remains in effect after reloading the page in the same browser.
- [ ] With no saved theme preference, the game starts in its current light appearance.
- [ ] Invalid or absent theme preference values do not prevent the game from loading; the light theme is used when the preference is invalid.
- [ ] Both themes correctly style the page, controls, grid, cards, score list, and completion dialog.
- [ ] The toggle is usable by keyboard and its current state is announced accessibly.
- [ ] Existing mouse and keyboard card controls, grid-size selection, timer, matching, rating, win flow, play-again action, and best-score behavior continue to work.
- [ ] Existing `memoryGameScores` data is unchanged by switching themes or reloading.
- [ ] The interface remains usable at the existing mobile and desktop breakpoints.

## Manual verification checklist

1. Open `memory-game.html`; confirm it still starts in the current light theme.
2. Switch to dark theme; check all page sections, both grid sizes, card faces and backs, focus styling, and the completion dialog.
3. Start a game, flip cards, and switch themes mid-game; confirm game state is preserved.
4. Reload the page; confirm the selected theme is restored.
5. Switch back to light theme and reload; confirm the light preference is restored.
6. Play through a game and verify moves, timer, rating, score saving, and best-score display.
7. Use Tab and Enter or Space to operate the theme toggle and play cards; confirm visible focus and normal keyboard behavior.
8. Check the layout at narrow and wide viewport sizes.

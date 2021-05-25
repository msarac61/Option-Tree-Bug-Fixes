# Wordpress Option Tree "Trying to access array offset on value of type bool" Error Solved

'Solved'

1. Go option-tree/includes
2. Open class-ot-settings.php
3. Find First Code - Replace Code

```
public function add_sections() {

	// Loop through options.
	foreach ( (array) $this->options as $option ) {

		// Loop through pages.
		foreach ( (array) $this->get_pages( $option ) as $page ) {

			// Loop through page sections.
			foreach ( (array) $this->get_sections( $page ) as $section ) {

				// Add each section.
				add_settings_section(
					$section['id'],
					$section['title'],
					array( $this, 'display_section' ),
					$page['menu_slug']
				);

			}
		}
	}

	return false;
}
```


```
public function add_sections() {

	// Loop through options.
	foreach ( (array) $this->options as $option ) {

		// Loop through pages.
		foreach ( (array) $this->get_pages( $option ) as $page ) {

			// Loop through page sections.
			foreach ( (array) $this->get_sections( $page ) as $section ) {

				// Add each section.
				add_settings_section(
					$section['id'] ?? '',
					$section['title'] ?? '',
					array( $this, 'display_section' ),
					$page['menu_slug']
				);

			}
		}
	}

	return false;
}
```

<script>
  import {
    Header,
    HeaderNav,
    HeaderNavItem,
    HeaderNavMenu,
    SkipToContent,
    HeaderActionLink,
    HeaderUtilities,
    Theme,
    HeaderAction,
    SideNav,
    SideNavItems,
    SideNavLink,
    SideNavMenuItem,
    SideNavMenu,
    SideNavDivider,
  } from 'carbon-components-svelte';
  import LogoGithub from 'carbon-icons-svelte/lib/LogoGithub.svelte';
  import SettingsAdjust from 'carbon-icons-svelte/lib/SettingsAdjust.svelte';

  let theme = 'white'; // "white" | "g10" | "g80" | "g90" | "g100"

  $: document.documentElement.setAttribute('theme', theme);

  let isSideNavOpen = false;
</script>

<Header
  company="BPMTOMS"
  platformName="Convert BPM to MS"
  bind:isSideNavOpen
>
  <svelte:fragment slot="skip-to-content">
    <SkipToContent />
  </svelte:fragment>
  <HeaderNav>
    <HeaderNavItem href="/" text="Link 1" />
    <HeaderNavItem href="/" text="Link 2" />
    <HeaderNavItem href="/" text="Link 3" />
    <HeaderNavMenu text="Menu">
      <HeaderNavItem href="/" text="Link 1" />
      <HeaderNavItem href="/" text="Link 2" />
      <HeaderNavItem href="/" text="Link 3" />
    </HeaderNavMenu>
  </HeaderNav>
  <HeaderUtilities>
    <HeaderAction icon={SettingsAdjust} ref={theme}>
      <Theme
        bind:theme
        persist
        persistKey="__carbon-theme"
        render="toggle"
        toggle={{
          themes: ['white', 'g90'],
          labelA: 'Enable dark mode',
          labelB: 'Enable dark mode',
          hideLabel: true,
          size: 'sm',
        }}
      />
    </HeaderAction>
    <HeaderActionLink
      href="https://github.com/Ocknyer/BpmToMs_Svelte"
      icon={LogoGithub}
      target="_blank"
    />
  </HeaderUtilities>
</Header>

<SideNav bind:isOpen={isSideNavOpen}>
  <SideNavItems>
    <SideNavLink href="/" text="Link 1" />
    <SideNavLink href="/" text="Link 2" />
    <SideNavLink href="/" text="Link 3" />
    <SideNavMenu text="Menu">
      <SideNavMenuItem href="/" text="Link 1" />
      <SideNavMenuItem href="/" text="Link 2" />
      <SideNavMenuItem href="/" text="Link 3" />
    </SideNavMenu>
    <SideNavDivider />
    <SideNavLink text="Link4" />
  </SideNavItems>
</SideNav>

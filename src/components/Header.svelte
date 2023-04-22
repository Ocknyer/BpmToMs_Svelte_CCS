<script>
  import {
    Header,
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

  // $: document.documentElement.setAttribute('theme', theme);

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
  <HeaderUtilities>
    <HeaderAction icon={SettingsAdjust}>
      <Theme
        render="toggle"
        persist
        persistKey="__carbon-theme"
        toggle={{
          themes: ['white', 'g80'],
          labelA: 'Enable dark mode',
          labelB: 'Enable dark mode',
          hideLabel: true,
          size: 'sm',
        }}
      />
    </HeaderAction>
    <HeaderActionLink
      href="https://github.com/Ocknyer/BpmToMs_Svelte_CCS"
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
    <SideNavMenu text="Set Lists">
      <SideNavMenuItem href="/" text="Link 1" />
      <SideNavMenuItem href="/" text="Link 2" />
      <SideNavMenuItem href="/" text="Link 3" />
    </SideNavMenu>
    <SideNavDivider />
    <SideNavLink text="Link4" />
  </SideNavItems>
</SideNav>

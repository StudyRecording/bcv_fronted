<script>
    import Login from '$lib/login/Login.svelte';
    import { ButtonGroup, Button, DarkMode, Navbar, NavBrand, NavLi, NavUl, NavHamburger, Avatar, Dropdown, DropdownItem, DropdownHeader, DropdownDivider } from 'flowbite-svelte';
    // 登录弹窗
    let formModal = $state(false);
    // 登录状态
    let loginstatus = $state(false);

    // 登录方法
    function loginclick() {
      formModal = false;
      loginstatus = true;
    }
</script>
  
<Navbar>
  <NavBrand href="/">
    <!-- <img src="/images/flowbite-svelte-icon-logo.svg" class="me-3 h-6 sm:h-9" alt="Flowbite Logo" /> -->
    <span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">BCV</span>
  </NavBrand>
  <div class="{loginstatus ? 'flex' : 'hidden'} items-center md:order-2">
    <DarkMode />
    <Avatar id="avatar-menu" src="https://picsum.photos/200" class="ml-5"/>
    <NavHamburger class1="w-full md:flex md:w-auto md:order-1" />
  </div>
  <div class="{loginstatus ? 'hidden' : 'flex'} md:order-2">
    <DarkMode />
    <ButtonGroup size="sm" class="ml-5">
      <Button size="sm" on:click={() => (formModal = !formModal)} >登录</Button>
      <Button size="sm" color="primary">注册</Button>
    </ButtonGroup>
    <NavHamburger />
  </div>
  <Dropdown placement="bottom" triggeredBy="#avatar-menu">
    <DropdownHeader>
      <span class="block text-sm">Bonnie Green</span>
      <span class="block truncate text-sm font-medium">name@flowbite.com</span>
    </DropdownHeader>
    <DropdownItem>Dashboard</DropdownItem>
    <DropdownItem>Settings</DropdownItem>
    <DropdownItem>Earnings</DropdownItem>
    <DropdownDivider />
    <DropdownItem>Sign out</DropdownItem>
  </Dropdown>
  <NavUl>
    <NavLi href="/" active={true}>首页</NavLi>
    <NavLi href="/book">书籍</NavLi>
    <NavLi href="/comic">漫画</NavLi>
    <NavLi href="/video">视频</NavLi>
  </NavUl>
</Navbar>

<Login {formModal} {loginclick}/>
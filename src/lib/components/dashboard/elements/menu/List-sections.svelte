<ul>
    <li>
        <a href="#">
            <i class="bx bx-home-smile" />
            <p class="text nav-text">Dashboard</p>
        </a>
    </li>
    <li>
        <a href="#">
            <i class="bx bx-bar-chart-alt-2" />
            <p class="text nav-text">Revenue</p>
        </a>
    </li>
    <li>
        <a href="#">
            <i class="bx bx-bell" />
            <p class="text nav-text">Notifications</p>
        </a>
    </li>
    <li>
        <a href="#">
            <i class="bx bx-pie-chart-alt" />
            <p class="text nav-text">Analytics</p>
        </a>
    </li>
    <li>
        <a href="#">
            <i class="bx bx-heart" />
            <p class="text nav-text">Likes</p>
        </a>
    </li>
    <li>
        <a href="#">
            <i class="bx bx-wallet" />
            <p class="text nav-text">Wallets</p>
        </a>
    </li>
</ul>

<style>
    /* SIDEBAR GENERAL */
    i {
        display: grid;
        place-items: center;
        font-size: 20px;
        margin-right: 20px;
        margin-left: 20px;
    }

    i,
    p {
        color: var(--text-color);
        transition: var(--tran-02);
        font-family: var(--fonts);
    }

    li {
        height: 50px;
        margin-top: 10px;
        list-style: none;
        display: flex;
        align-items: center;
    }

    a {
        height: 100%;
        width: 100%;
        display: flex;
        align-items: center;
        text-decoration: none;
        border-radius: 6px;
        transition: var(--tran-04);
    }

    a:hover {
        background-color: var(--primary-color);
    }

    a:hover p,
    a:hover i {
        color: var(--white);
    }

    /* SIDEVAR CLOSED */
    section.hidden .menu-container ul li a p{
        display: none;
    }

</style>
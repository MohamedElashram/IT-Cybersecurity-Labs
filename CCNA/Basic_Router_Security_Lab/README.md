# Basic Router Configuration

## Objective

Configure basic password security on a Cisco router, including:

- Enable password
- Enable secret
- Console password
- Password encryption

## Lab Topology

```text
PC ───────── R1
```

## Configuration

### 1. Configure Enable Password

```cisco
R1> enable
R1# configure terminal
R1(config)# enable password cisco
```

The `enable password` command protects access to privileged EXEC mode.

---

### 2. Encrypt Plaintext Passwords

```cisco
R1(config)# service password-encryption
```

This command encrypts plaintext passwords stored in the running configuration.

---

### 3. Configure Enable Secret

```cisco
R1(config)# enable secret cisco
```

`enable secret` provides a more secure password for privileged EXEC mode than `enable password`.

If both are configured, Cisco IOS uses the `enable secret` password.

---

### 4. Configure Console Password

```cisco
R1(config)# line console 0
R1(config-line)# password ccna
R1(config-line)# login
```

This configuration requires a password when accessing the router through the console.

---

## Verification

Use the following commands to verify the configuration:

```cisco
show running-config
```

Check that the password configuration appears in the running configuration.

You can also test the console password by exiting the console session and reconnecting.

## Key Concepts

| Command | Purpose |
|---|---|
| `enable password` | Configures a privileged EXEC password |
| `enable secret` | Configures a more secure privileged EXEC password |
| `service password-encryption` | Encrypts plaintext passwords in the configuration |
| `line console 0` | Enters console-line configuration mode |
| `password` | Sets the line password |
| `login` | Enables password authentication on the line |
| `show running-config` | Displays the current configuration |

## What I Learned

- Difference between `enable password` and `enable secret`
- How to protect privileged EXEC mode
- How to configure console authentication
- How `service password-encryption` affects passwords in the configuration
- How to verify router configuration using `show running-config`

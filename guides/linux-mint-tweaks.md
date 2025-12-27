Ctrl+Shift+V To Preview

# Linux Mint Tweaks

These are several tweaks that will help optimize Linux Mint installed on your computer. Most part are optional and it's up to you.

## Enable SSD TRIM (if supported)

TRIM is a special feature designed to solve issue where the files deleted on an SSD (Solid-State Drive) does not fully erased the data right away, and only marks it as available while the the deleted data files remains until its overwritten. This will cause the SSD to slow down overtime because it has to clear the data first before writting new ones.

With TRIM, it enables the SSD to know which blocks of data are no longer available, and allows the SSD to erase them in advance.

In short, TRIM helps an SSD to be fast and performant by cleaning up after itself.

Start by running the command below:

```bash
sudo fstrim -v /
```

If your SSD supports TRIM, you'll see how many bytes were trimmed. If not, you might see an error or no output. E.g:

```
❯ sudo fstrim -v / 
/: 106.3 GiB (114093989888 bytes) trimmed
```

If your system supports TRIM, run the commands:

```
sudo systemctl enable fstrim.timer
sudo systemctl start fstrim.timer
```

To check the status, run:

```
systemctl status fstrim.timer
```

